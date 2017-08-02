---
title: "在 Visual Studio 中使用 C++ 和 Python | Microsoft Docs"
ms.custom: 
ms.date: 3/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7dbda92-21bf-4af0-bb34-29b8bf231f32
description: "在 Visual Studio 中编写适用于 Python 的 C++ 扩展或模块的过程和步骤"
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: f8a0bef07667e5f876473c966ed3d14a1b84dd0b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="creating-a-c-extension-for-python"></a>创建适用于 Python 的 C++ 扩展

使用 C++（或 C）编写的模块常用于扩展 Python 解释器的功能和启用对低级别操作系统功能的访问。 主要有以下 3 种类型的模块：

- 加速器模块：Python 是一种解释型语言，某些代码段可使用 C++ 进行编写来提高性能。 
- 包装器模块：向 Python 代码公开现有 C/C++ 接口，或公开更“Python 化”的 API，其利用 Python 语言功能使 API 更易于使用。
- 低级别系统访问模块：用于访问 CPython 运行时的较低级别功能、操作系统或基础硬件。 

本主题介绍了如何为 CPython 生成 C++ 扩展模块，该模块计算双曲正切并从 Python 代码中调用它。 为了演示性能差异，首先需使用 Python 创建和测试例程。

此处采用的方法适用于 [Python 文档](https://docs.python.org/3/c-api/)中所述的标准 CPython 扩展。 本主题末尾的[替代方法](#alternative-approaches)下将此方法与其他方法进行了比较。

## <a name="prerequisites"></a>先决条件

本演练针对的是包含“C++ 桌面开发”和“Python 开发”工作负载及其默认选项（如作为默认解释器的 Python 3.6）的 Visual Studio 2017。 在 **Python 开发**工作负载中，还可以选中右侧的“Python 本机开发工具”复选框，以设置本主题中所述的大多数选项。 （此选项还自动包括 C++ 工作负载。） 

![选择“Python 本机开发工具”选项](~/docs/python/media/cpp-install-native.png)

有关详细信息，请参阅[安装针对 Visual Studio 的 Python 支持](installation.md)，其中包括使用其他版本的 Visual Studio。 如果单独安装 Python，请务必在安装程序的“高级选项”下选择“下载调试符号”和“下载调试二进制文件”。 这可确保在选择进行调试生成时能够使用必要的调试库。

> [!Note]
> 还可以通过“数据科学和分析应用程序”工作负载使用 Python，此工作负载默认包含 Anaconda 3 64 位（含有最新版 CPython）和“Python 本机开发工具”选项。

## <a name="create-the-python-application"></a>创建 Python 应用程序

1. 在 Visual Studio 中创建新的 Python 项目，方法是选择“文件”>“新建”>“项目”菜单命令，然后搜索“Python”，选择“Python 应用程序”模板，指定合适的名称和位置，然后选择“确定”。

1. 在项目的 `.py` 文件中，粘贴以下代码，用于对双曲正切的计算进行基准测试（无需使用数学库即可实现，以便简化比较）。 可随意手动输入代码，体验某些 [Python 编辑功能](code-editing.md)。

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 100000
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tanger function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()

        result = fn(DATA)

        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. 使用“调试”>“开始执行(不调试)”(Ctrl+F5) 运行程序以查看结果。 可看到每个基准测试需要几秒钟才能完成。

## <a name="create-the-core-c-project"></a>创建核心 C++ 项目

1. 在解决方案资源管理器中右键单击解决方案，然后选择“添加”>“新建项目...”。 Visual Studio 解决方案可以同时包含 Python 和 C++ 项目。

1. 搜索“C++”，选择“空项目”，指定名称（例如 TanhBenchmark），然后选择“确定”。 注意：如果随 Visual Studio 2017 一起安装了 **Python 本机开发工具**，则可从 **Python 扩展模块**模板开始，其中有许多现成的此处所述内容。 但是，对于本演练，从空项目开始可以逐步演示如何生成扩展模块。

1. 在新项目中创建 C++ 文件，方法是右键单击“源文件”节点，然后选择“添加”>“新建项...”，选择“C++ 文件”，指定其名称（例如 `module.cpp`），然后选择“确定”。 若要在后续步骤中打开 C++ 属性页，则必须执行此步骤。

1. 右键单击新项目并选择“属性”，然后在显示的“属性页”对话框顶部，将“配置”设置为“所有配置”。

1. 按如下所述设置特定属性，然后选择“应用”（可能需要单击“应用”按钮可编辑字段的外部才能成功启用）。

    | Tab | 属性 | 值 | 
    | --- | --- | --- |
    | 常规 | 常规 > 目标名称 | 将此设置为与 Python 看到的模块名称完全匹配。 |
    | | 常规 > 目标扩展名 | .pyd |
    | | 项目默认值 > 配置类型 | 动态库(.dll) |
    | C/C++ > 常规 | 附加包含目录 | 根据相应的安装添加 Python `include` 文件夹，例如 `c:\Python36\include` |     
    | C/C++ > 代码生成 | 运行库 | 多线程 DLL (/MD)（请参阅下面的“警告”） |
    | C/C++ > 预处理器 | 预处理器定义 | 将 `Py_LIMITED_API;` 添加到字符串开头。 这会限制可从 Python 调用的某些函数，并使代码在 Python 不同版本之间更易于移植。 |
    | 链接器 > 常规 | 附加库目录 | 根据相应的安装添加包含 `.lib` 文件的 Python `lib` 文件夹，例如 `c:\Python36\libs`。 （务必指向包含 `.lib` 文件的 `libs` 文件夹，而非包含 `.py` 文件的 `Lib` 文件夹。） | 

    > [!Tip]
    > 如果未看到 C/C++ 选项卡，这是因为项目不包含标识为 C/C++ 源文件的任何文件。 如果创建的源文件不含 `.c` 或 `.cpp` 扩展名，则可能出现这种情况。 例如，如果之前在“新建项”对话框中不小心输入了 `module.coo`（而不是 `module.cpp`），则 Visual Studio 会创建文件，但不会将文件类型设置为“C/C+ 代码”，而正是它激活 C/C++ 属性选项卡。 即使将文件重命名为带 `.cpp`，也不会起作用。 若要更正此问题，请在解决方案资源管理器中右键单击文件，选择“属性”，然后将“文件类型”设置为“C/C++ 代码”。

    > [!Warning]
    > 即使对于调试配置，也不要将“C/C++”>“代码生成”>“运行时库”选项设置为“多线程调试 DLL (/MDd)”。 需要选择“多线程 DLL (/MD)”运行时，因为必须使用此选项才能生成非调试 Python 二进制文件。 如果碰巧设置了 /MDd 选项，则会在生成 DLL 的调试配置时看到错误“C1189: Py_LIMITED_API 与 Py_DEBUG、Py_TRACE_REFS 和 Py_REF_DEBUG 不兼容”。 此外，如果删除 `Py_LIMITED_API` 来避免出现生成错误，则在尝试导入模块时，Python 将崩溃。 （如下所述，崩溃将发生在 DLL 对 `PyModule_Create` 的调用中，并出现输出消息“严重 Python 错误: PyThreadState_Get: 无当前线程”。）
    >
    > 请注意，/MDd 选项用于生成 Python 调试二进制文件（例如 python_d.exe），但对扩展 DLL 选择此选项仍会导致 `Py_LIMITED_API` 的生成错误。
   
1. 右键单击 C++ 项目，然后选择“生成”以测试配置（包括“调试”和“发布”）。 请注意，将在解决方案文件夹中的“调试”和“发布”下找到 `.pyd` 文件，而非 C++ 项目文件夹本身。

1. 将以下代码添加到 C++ 项目的主 `.cpp` 文件：

    ```cpp
    #include <Windows.h>
    #include <cmath>    

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh(x) {
        return sinh(x) / cosh(x);
    }
    ```

1. 再次生成 C++ 项目以确认代码正确。


## <a name="convert-the-c-project-to-an-extension-for-python"></a>将 C++ 项目转换为适用于 Python 的扩展

若要使 C++ DLL 成为适用于 Python 的扩展，需要修改导出的方法以与 Python 类型进行交互。 然后，需要添加一个可导出模块的函数以及该模块的方法的定义。 有关此处所显示内容的背景信息，请参阅 python.org 上的 [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html)（Python/C API 参考手册）和重点的 [Module Objects](https://docs.python.org/3/c-api/module.html)（模块对象）。 （务必从右上角的下拉控件中选择相应 Python 版本。）

1. 在 C++ 文件的顶部，添加 `Python.h`：

    ```cpp
    include <Python.h>
    ```

1. 修改 `tanh` 方法以接受和返回 Python 类型：

    ```cpp
    PyObject* tanh(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. 添加一个定义如何向 Python 呈现 C++ `tanh` 函数的结构：

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. 添加一个定义 Python 以何种形式看到模块的结构：

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. 添加 Python 加载模块时要调用的方法，该模块必须命名为 `PyInit_<module-name>`，其中 *&lt;module_name&gt;* 与 C++ 项目的“常规”>“目标名称”属性完全匹配（也就是说，其与项目生成的 `.pyd` 的文件名相匹配）。

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. 再次生成 DLL 以验证代码。

## <a name="test-the-code-and-compare-the-results"></a>测试代码和比较结果

将 DLL 结构化为 Python 扩展后，便可从 Python 项目引用该扩展，导入模块，并使用其方法。

可通过两种方法使 DLL 可供 Python 使用。 第一，可将引用从 Python 项目添加到 C++ 项目，前提是它们位于同一个 Visual Studio 解决方案中：

1. 在解决方案资源管理器中，右键单击 Python 项目，然后选择“引用”。 在对话框中，依次选择“项目”选项卡、“superfastcode”项目，然后选择“确定”。

第二，可在全局 Python 环境中安装模块，使其也可供其他 Python 项目使用。 请注意，此操作通常需要刷新该环境的 IntelliSense 完成数据库，并从环境中删除模块。

1. 如果使用 Visual Studio 2017，请运行 Visual Studio 安装程序，选择“修改”，然后选择“各个组件”>“编译器、生成工具和运行时”>“Visual C++ 2015.3 v140 工具集”。 这是因为 Python（适用于 Windows）本身是使用 Visual Studio 2015（版本 14.0）构建的，并期望通过此处所述的方法生成扩展时能够使用这些工具。

1. 在 C++ 项目中创建名为 `setup.py` 的文件，方法是右键单击项目，选择“添加”>“新建项...”**，搜索“Python”，然后选择“Python 文件”**，将其命名为 setup.py，然后选择“确定”。 当编辑器中出现该文件时，将以下代码粘贴到其中：

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ Extension',
        ext_modules = [sfc_module]
        )
    ```

    请参阅 [Building C and C++ Extentions](https://docs.python.org/3/extending/building.html)（生成 C 和 C++ 扩展）(python.org)，获取此脚本相关文档。

1. `setup.py` 代码指示 Python 从命令行生成扩展（使用 Visual Studio 2015 C++ 工具集）。 打开提升的命令提示符，导航到包含 C++ 项目（和 `setup.py`）的文件夹，然后输入以下命令：

    ```bash
    pip install .
    ```

现在，可调用模块的 `tanh` 代码，并将其性能与 Python 实现进行比较：

1. 在 `tanhbenchmark.py` 中添加以下行以调用从 DLL 导出的 `fast_tanh` 方法，并将其添加到基准输出中。 如果手动键入 `from s` 语句，则将在完成列表中看到 `superfastcode` 出现，并在键入 `import` 后看到 `fast_tanh` 方法。

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. 运行 Python 程序，可看到 C++ 例程的运行速度比 Python 实现快 15 到 20 倍。

## <a name="debug-the-c-code"></a>调试 C++ 代码

[Visual Studio 中的 Python 支持](installation.md)包括可[同时调试 Python 和 C++ 代码](debugging-mixed-mode.md)。 若要体验此功能，请执行以下操作：

1. 在解决方案资源管理器中，右键单击 Python 项目，依次选择“属性”、“调试”选项卡，然后选择“调试”>“启用本机代码调试”选项。

    > [!Tip]
    > 启用本机代码调试后，Python 输出窗口可能在程序完成后立即消失，而不出现通常的“按任何键以继续...”暂停界面。 若要强制暂停，请在启用本机代码调试后，向“调试”选项卡上的“运行”>“解释器参数”字段添加 `-i` 选项。 这会在代码完成后将 Python 解释器置于交互模式，此时它将等待你按 Ctrl+Z, Enter 以退出。 （或者，如果不介意修改 Python 代码，则可在程序结束时添加 `import os` 和 `os.system("pause")` 语句。 这会复制初始的暂停提示符。）

1. 在 C++ 代码的 `tanh` 方法内的第 1 行设置一个断点，然后启动调试器。 该代码被调用时，调试器将停止：

    ![在 C++ 代码中的断点处停止](~/docs/python/media/cpp-debugging.png)

1. 此时，可浏览 C++ 代码、检查变量等，[同时调试 Python 和 C++](debugging-mixed-mode.md) 中对此进行了详细介绍。

## <a name="alternative-approaches"></a>替代方法 

下表描述了创建 Python 扩展的其他方法。 本主题已经讨论了 CPython 的第一项。

| 方法 | 年份 | 代表用户 | 优点 | 缺点 |
| --- | --- | --- | --- | --- |
| 适用于 CPython 的 C/C++ 扩展模块 | 1991 | 标准库 | [丰富的文档和教程](https://docs.python.org/3/c-api/)。 完全控制。 | 编译、可移植性、引用管理。 扎实的 C 知识。 |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 针对多种语言立即生成绑定。 | 如果 Python 是唯一目标，则开销过大。 |
| ctype | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 无编译，广泛可用性。 | 访问和转变 C 结构的过程比较繁琐且容易出错。 |
| Cython | 2007 | [gevent](http://www.gevent.org/)、[kivy](https://kivy.org/) | 类似于 Python。 非常成熟。 高性能。 | 编译、新语法和工具链。 |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/)、[pypy](http://pypy.org/) | 易于集成，与 PyPy 兼容。 | 新推出，不够成熟。 |

