---
title: "Visual Studio 中 Python 的混合模式调试 | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca86a87-e254-4ab7-b3ba-a0ab99c1da93
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
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: 9e8ac0cbafe296223de68eb5b4f1b89680f61088
ms.contentlocale: zh-cn
ms.lasthandoff: 05/23/2017

---

# <a name="debugging-python-and-c-together"></a>一起调试 Python 和 C++

大多数常规 Python 调试器支持仅调试 Python 代码。 但实际上，Python 结合 C 或 C++ 一起使用时需要高性能或能够直接调用平台 API（请参阅[创建适用于 Python 的 C++ 扩展](cpp-and-python.md)以查看示例）。 加载 Python 项目时，Visual Studio 具有合并调用堆栈、能够在 Python 和本机代码之间进行单步执行、在任一类型的代码中产生断点，还能够查看本机帧中对象的 Python 表示形式（反之亦然），为 Python 和本机 C/C++ 提供集成的同时混合模式调试：

![混合模式调试](~/python/media/mixed-mode-debugging.png) 

有关使用 Visual Studio 生成、测试和调试本机 C 模块的介绍，请参阅[深入了解：创建本机模块](https://youtu.be/D9RlT06a1EI)（youtube.com，9 分 9 秒）。

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

> [!Note]
> 针对 Visual Studio 1.x 的 Python 工具不提供混合模式调试。

## <a name="enabling-mixed-mode-debugging"></a>启用混合模式调试

1. 在解决方案资源管理器中右键单击项目，选择“属性”，选择“调试”选项卡，然后打开“启用本机代码调试”选项。 这将针对所有调试会话启用混合模式。

    ![启用本机代码调试](~/python/media/mixed-mode-debugging-enable-native.png)

    > [!Tip]    
    > 启用本机代码调试后，Python 输出窗口可能在程序完成后立即消失，而不出现通常的“按任何键以继续...”暂停界面。 若要强制暂停，请在启用本机代码调试后，向“调试”选项卡上的“运行”>“解释器参数”字段添加 `-i` 选项。 这会在代码完成后将 Python 解释器置于交互模式，此时它将等待你按 Ctrl+Z, Enter 以退出。

1. 将混合模式调试器附加到现有进程（“调试”>“附加到进程...”）时，选择“选择...”按钮以打开“选择代码类型”对话框，设置“调试这些代码类型”选项，然后在列表中选择**本机** 和 **Python**：

    ![选择本机和 Python 代码类型](~/python/media/mixed-mode-debugging-code-type.png)

    代码类型设置是永久的，因此如果稍后附加到其他进程时想要禁用混合模式调试，需要重复这些步骤并清除 Python 代码类型。

    除**本机**代码类型还可以选择其他代码类型，或者不选择本机代码类型。 例如，如果托管应用程序承载 CPython，后者又使用本机扩展模块，并且你想要调试所有三种类型，则可以一起勾选“Python”、“本机”和“托管”，以获得统一调试体验，其中包括合并调用堆栈以及在所有三个运行时之间进行单步执行。

1. 首次在混合模式下开始调试时，可能会看到“需要 Python 符号”对话框。 有关详细信息，请参阅[混合模式调试的符号](debugging-symbols-for-mixed-mode.md)。 你只需为任何给定的 Python 环境安装一次符号。 请注意，如果通过 Visual Studio 2017 安装程序安装 Python 支持，则符号会自动包括在其中。

1. 可能还需其自身具备现成的 Python 源代码。 对于标准 Python，可从 [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/) 获取。 下载适合版本的存档，并将其提取到文件夹中。 无论系统何时发出提示，都需将 Visual Studio 指向该文件夹中的特定文件。

> [!Note]
> 仅当在 Visual Studio 中加载了 Python 项目时，才会启用此处所述的混合模式调试。 该项目决定了 Visual Studio 的调试模式，并提供了混合模式选项。 但是，如果已加载 C++ 项目（就像[如 python.org 中所述，在另一应用程序中嵌入 Python 时一样](https://docs.python.org/3/extending/embedding.html)），Visual Studio 将使用不支持混合模式调试的本机 C++ 调试程序。
>
> 这种情况下，启动 C++ 项目，但不进行调试（“调试”>“启动但不调试”或 Ctrl+F5），然后使用“调试”>“附加到进程...”。 在出现的对话框中，选择相应的进程，然后使用“选择...”按钮来打开“选择代码类型”对话框，在其中选择 Python，如下所示。 选择“确定” 关闭对话框，然后选择“附加”，启动调试器。 请注意，有可能需要在 C++ 应用中引入适当的暂停或延迟，确保在附加到调试器之前，该应用不会调用要调试的 Python。
>
> ![附加调试器时选择 Python 作为调试类型](~/python/media/mixed-mode-debugging-attach-type.png)

## <a name="mixed-mode-specific-features"></a>混合模式特定功能

- [合并调用堆栈](#combined-call-stack)
- [在 Python 和本机代码之间进行单步执行](#stepping-between-python-and-native-code)
- [本机代码中的 PyObject 值视图](#pyobject-values-view-in-native-code)
- [Python 代码中的本机值视图](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>合并调用堆栈

“调用堆栈”窗口交叉显示本机和 Python 堆栈帧，同时标记两者间转换：

![合并调用堆栈](~/python/media/mixed-mode-debugging-call-stack.png)

> [!Note]
> 如果已设置“工具”>“选项”>“调试”>“常规”>“启用仅我的代码”选项，转换将显示为“[外部代码]”，但不指定转换方向。

如果可能，双击任何调用帧将使其处于活动状态，并打开相应的源代码。 如果源代码不可用，该帧仍将处于活动状态并可以检查局部变量。

### <a name="stepping-between-python-and-native-code"></a>在 Python 和本机代码间进行单步执行

使用单步执行 (F11) 或单步跳出 (Shift + F11) 命令时，混合模式调试器会正确处理代码类型间的更改。 例如，当 Python 调用在 C 中实现的类型的方法时，对该方法的调用进行的单步执行将在实现该方法的本机函数开头处停止。 当本机代码调用导致调用 Python 代码的某些 Python API 函数时也一样。 例如，对最初在 Python 中定义的函数值进行的单步执行 `PyObject_CallObject` 将在 Python 函数的开头处停止。 通过 [ctype](http://docs.python.org/3/library/ctypes.html) 从 Python 调用的本机函数也支持从 Python 到本机的单步执行。

### <a name="pyobject-values-view-in-native-code"></a>本机代码中的 PyObject 值视图

本机（C 或 C++）帧处于活动状态时，其局部变量将显示在调试器局部变量窗口中。 在本机 Python 扩展模块中，许多模块属于 `PyObject` 类型（即 `_object` 的 typedef），或其他几个基础的 Python 类型（请参阅下面的列表）。 在混合模式调试中，这些值表示标记了“Python 视图”的其他子节点。 如果在 Python 帧中表示局部变量引用同一对象，展开时，此节点将显示该变量的 Python 表示形式，与应看到的完全一致。 此节点的子级可编辑。

![Python 视图](~/python/media/mixed-mode-debugging-python-view.png)

若要禁用此功能，单键单击局部变量窗口中的任何位置并切换“Python”>“显示 Python 视图节点”菜单选项：

![启用 Python 视图](~/python/media/mixed-mode-debugging-enable-python-view.png)

显示“[Python 视图]”节点的 C 类型（如果已启用）：

- `PyObject `
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

“[Python 视图]”不会为你自行创作的类型自动显示。 为 Python 3.x 创作扩展时，这通常不成问题，因为任何对象最终都具有上述类型之一的 `ob_base` 字段，这将导致显示“[Python 视图]”。 

但是对于 Python 2.x，每个对象类型通常将其标头声明为内联字段的集合，并且在 C/C++ 代码中的类型系统级别的自定义创作类型和 `PyObject` 之间没有任何关联。 若要为此类自定义类型启用“[Python 视图]”节点，请在 [Python 工具安装目录](installation.md#install-locations)中编辑 `PythonDkm.natvis`，然后只需为 C 构造或 C++ 类在 XML 中添加其他元素即可。

其他（更优）选项为遵循 [PEP 3123](http://www.python.org/dev/peps/pep-3123/) 并使用显式 `PyObject ob_base;` 字段而非 `PyObject_HEAD`，但因为向后兼容性的原因，因此不可能总是采用这种选项。


### <a name="native-values-view-in-python-code"></a>Python 代码中的本机值视图

类似上一节，当 Python 帧处于活动状态时，你可以为局部变量窗口中的本机值启用“[C++ 视图]”。 默认情况下未启用此功能，因此可通过在局部变量窗口中单击右键并切换“Python”>“显示 C++ 视图节点”菜单选项来启用此功能。

![启用 C++ 视图](~/python/media/mixed-mode-debugging-enable-cpp-view.png)

“[C++ 视图]”节点提供值的基础 C/C++ 结构的表示形式，该形式与本机帧中的一致。 例如，它针对 Python 长整型显示 `_longobject` 的实例（`PyLongObject` 是其 typedef），并且它将尝试推断自行创作的本机类的类型。 此节点的子级可编辑。

![C++ 视图](~/python/media/mixed-mode-debugging-cpp-view.png)

如果一个对象的子字段属于 `PyObject` 类型或其他支持的类型之一，则它将具有一个“[Python 视图]”表示形式节点（如果已启用），从而在未向 Python 直接公开链接时可以导航对象关系图。

与使用 Python 对象元数据来确定对象类型的“[Python 视图]”节点不同，“[C++ 视图]”没有类似的可靠机制。 通常情况下，若给定一个 Python 值（即 `PyObject` 引用），不可能可靠地确定哪个 C/C++ 结构支持它。 混合模式调试器尝试通过查看具有函数指针类型的对象类型（例如，其 `ob_type` 字段引用的 `PyTypeObject`）的各字段猜测该类型。 如果其中一个函数指针引用可解析的函数，且该函数具有类型比 `PyObject*` 更具体的 `self` 参数，则认为该类型为后备类型。 例如，如果给定对象的 `ob_type->tp_init` 指向以下函数：

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

则调试器可正确推断该对象的 C 类型为 `FobObject`。 如果无法根据 `tp_init` 确定更精确的类型，它将移到其他字段。 如果无法通过所有这些字段推断类型，“[C++ 视图]”节点会将该对象作为 `PyObject` 实例显示。

若要始终获得自定义创作类型的有用表示形式，注册类型时最好注册至少一个特殊函数，并使用强类型 `self` 参数。 大多数类型可自然地满足该要求；如果无法满足，则 `tp_init` 通常是实现此目的最方便的选项。 针对单独显示的类型虚拟实现 `tp_init` 以启用调试类型推理只能立即返回零，如上述代码示例所示。

## <a name="differences-from-standard-python-debugging"></a>与标准 Python 调试的区别

混合模式调试器不同于[标准 Python 调试器](debugging.md)，因为它引入了一些其他功能，但缺少某些 Python 相关功能：

- 不支持的功能：条件断点、调试交互窗口和跨平台远程调试。
- 即时窗口：可用但其功能有限，包括此处列出的所有限制。
- 支持的 Python 版本：仅限 CPython 2.7 和 3.3+。
- Visual Studio Shell：将 Visual Studio Shell 与 Python 配合使用时（例如，如果已使用集成安装程序安装），Visual Studio 无法打开 C++ 项目，且 C++ 文件的编辑体验只是一个基本的文本编辑器。 但是，在调试器窗口中含源代码、单步执行本机代码和 C++ 表达式评估的 Shell 中完全支持 C/C++ 调试和混合模式调试。
- 查看和扩展对象：在局部变量和监视调试器工具窗口中查看 Python 对象时，混合模式调试器仅显示对象的结构。 它不会自动评估属性，也不会显示计算特性。 对于集合，它仅显示内置集合类型的元素（`tuple`、`list`、`dict` 和 `set`。 自定义集合类型不会可视化为集合，除非它们继承自某些内置集合类型。
- 表达式评估：请参阅下文。

### <a name="expression-evaluation"></a>表达式评估

标准 Python 调试器允许在调试进程在代码的任何位置暂停时评估监视窗口和即时窗口中的任意 Python 表达式，前提是它在 I/O 操作或其他类似系统调用中不会被阻止。 在混合模式调试中，仅当代码出现断点或进行单步执行后，任意表达式在 Python 代码中停止时，才进行评估，且只在发生断点或单步执行操作的线程上评估表达式。

当在上述条件不适用的本机代码或 Python 代码中停止时（例如，在单步跳出操作后或在其他线程上），表达式评估将限于访问当前所选帧中的局部变量和全局变量、访问其他字段以及使用文本索引内置集合类型。 例如，下面的表达式可以在任何上下文中进行评估（前提是所有标识符引用现有变量和相应类型的字段）：

```python
foo.bar[0].baz['key']
```

混合模式调试器还会以不同的方式解析此类表达式。 所有成员访问操作都只查找直接属于对象的字段（如 `__dict__` 或 `__slots__` 中的项，或通过 `tp_members` 向 Python 公开的本机结构字段），并忽略所有 `__getattr__``__getattribute__` 或描述符逻辑。 同样，所有索引操作将忽略 `__getitem__`，并直接访问集合的内部数据结构。

为了保持一致性，此名称解析方案用于匹配有限表达式评估约束的所有表达式，不考虑当前停止点是否允许任意表达式。 当全功能计算器可用时，若要强制正确的 Python 语义，请使用括号将该表达式括起来：

```python
(foo.bar[0].baz['key'])
```
