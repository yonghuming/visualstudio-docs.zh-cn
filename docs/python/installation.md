---
title: "在 Visual Studio 中安装 Python | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 613af31a2e44cc447980b68de4b0b5642dde1262
ms.contentlocale: zh-cn
ms.lasthandoff: 07/18/2017

---

# <a name="installing-python-support-in-visual-studio-on-windows"></a>在 Windows 上的 Visual Studio 中安装 Python 支持

若要安装针对 Visual Studio 的 Python 支持，请按照与你的 Visual Studio 版本匹配的部分中的说明进行操作：

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 及更早版本](#visual-studio-2013-and-earlier)

对于 Visual Studio 2015 及更早版本，还需要单独安装所选的 Python 解释器。 有关详细信息，请参阅 [Python 环境](python-environments.md)。

若要在执行安装步骤后快速测试 Python 支持，请按 Alt-I 并输入 `2+2` 打开 Python 交互式窗口。 如果看不到输出 `4`，请重新检查步骤。

> [!Tip]
> Python 工作负载包括有用的 Cookiecutter 扩展，扩展提供图形用户界面以发现模板、输入模板选项及创建项目和文件。 有关详细信息，请参阅[使用 Cookiecutter](cookiecutter.md)。

> [!Note]
> 目前尚未在 Visual Studio for Mac 中提供 Python 支持，但可在 Mac 和 Linux 上通过 Visual Studio Code 获取相应支持。 请参阅[问题和解答](python-in-visual-studio.md#questions-and-answers)。

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. 从 [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/) 安装 Visual Studio 2017。

1. 在 Visual Studio 安装程序中，选择“Web 和云”>“Python 开发”工作负载。

    ![Visual Studio 安装程序中的 Python 开发工作负载](media/installation-python-workload.png)

    > [!Note]
    > Python 也包含在**数据科学和分析应用程序**工作负载中。

1. 在安装程序的右侧，选择 Python 解释器和想要包括其他相关工具。 例如，如果计划开发适用于 Python 的 C++ 扩展，请包括“Python 本机开发工具”选项。

    ![Visual Studio 安装程序中的 Python 开发选项](media/installation-python-options.png)

1. 如果计算机上已安装了解释器，请参阅[为现有解释器创建环境](python-environments.md#creating-an-environment-for-an-existing-interpreter)。

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. 通过“控制面板”>“程序和功能”，选择 **Microsoft Visual Studio 2015**，然后选择“更改”，从而运行 Visual Studio 安装程序。

1. 在安装程序中，选择“修改”。

1. 选择“编程语言”>“针对 Visual Studio 的 Python 工具”，然后选择“下一步”：

    ![Visual Studio 2015 安装程序中的 PTVS 选项](media/installation-vs2015.png)    

1. Visual Studio 安装程序完成后，[安装所选的 Python 解释器](python-environments.md#selecting-and-installing-python-interpreters)。 如果已安装了解释器，请参阅[为现有解释器创建环境](python-environments.md#creating-an-environment-for-an-existing-interpreter)。

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 及更早版本

1. 为你的 Visual Studio 版本安装相应版本的针对 Visual Studio 的 Python 工具：

    - Visual Studio 2013：[Visual Studio 2013 PTVS 2.2](https://github.com/Microsoft/PTVS/releases/v2.2)。 Visual Studio 2013 中的“文件”>“新建项目”对话框提供用于此过程的快捷方式。
    - Visual Studio 2012：[Visual Studio 2012 PTVS 2.1](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010：[Visual Studio 2010 PTVS 2.1](https://pytools.codeplex.com/downloads/get/920479)

1. [安装所选的 Python 解释器](python-environments.md#selecting-and-installing-python-interpreters)。 如果已安装了解释器，请参阅[为现有解释器创建环境](python-environments.md#creating-an-environment-for-an-existing-interpreter)。

## <a name="install-locations"></a>安装位置

默认情况下，为计算机上的所有用户安装 Python 支持。

对于 Visual Studio 2017，Python 工作负载安装在 `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` 中，其中 &lt;VS_edition&gt; 为社区版、专业版或企业版。

对于 Visual Studio 2015 及更早版本，安装路径如下所示：

- 32 位：
  - 路径：`%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 路径的注册表位置：`HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 位：
  - 路径：`%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 路径的注册表位置：`HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

其中：

- &lt;VS_ver&gt; 是：    
    - Visual Studio 2015 14.0
    - Visual Studio 2013 12.0
    - Visual Studio 2012 11.0
    - Visual Studio 2010 10.0
- &lt;PTVS_ver&gt; 是版本号，例如 2.2、2.1、2.0、1.5、1.1 或 1.0。

### <a name="user-specific-installations-15-and-earlier"></a>特定于用户的安装（1.5 及更早版本）

仅允许为当前用户安装针对 Visual Studio 的 Python 工具 1.5 版及更早版本，这种情况下的安装路径是 `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`，其中 &lt;VS_ver&gt; 和 &lt;PTVS_ver&gt; 与上文所述相同。

