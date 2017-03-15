---
title: "实现了源代码管理插件的最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件，最佳做法"
  - "最佳实践、 源代码管理插件"
  - "源代码管理 [Visual Studio SDK] 插件"
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 实现了源代码管理插件的最佳做法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

下面的技术详细信息可以帮助您可靠地实现了源代码管理插件中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 内存管理问题  
 在大多数情况下，集成的开发环境 \(IDE\)，即调用方释放并分配内存。 源代码管理插件在调用方分配的缓冲区中返回的字符串和其他项。 发生位置的特定函数的说明中注明了异常。  
  
## 文件的名称的数组  
 当传递的文件数组时，它将不传递作为连续的文件名称的数组。 它是作为传递的指针的数组给文件的名称。 例如，在 [SccGet](../extensibility/sccget-function.md), ，通过传递文件名称 `lpFileNames` 参数，其中 `lpFileNames` 是实际指向的指针 `char **`。`lpFileNames`\[0\] 是指向第一个名称 `lpFileNames`\[1\] 是指向第二个名称，依此类推。  
  
## 大型模型  
 所有指针都是 32 位，即使在 16 位操作系统上。  
  
## 完全限定的路径  
 其中的文件名或目录指定为参数，它们必须是完全限定的路径或 UNC 路径，不带结束反斜杠。 它负责的源代码管理插件将转换为如果，它是基础源代码控制系统的要求的相对路径。  
  
## 为已注册的 DLL 指定完全限定的路径  
 IDE 不会再从相对路径 \(例如，.\\NewProvider.dll\) 加载 Dll。 \(例如 C:\\Providers\\NewProvider.dll\)，必须指定 DLL 的完整路径。 此要求可增强通过阻止未经授权或模拟源控件 Dll 的加载的 IDE 的安全性。  
  
## 安装源代码管理插件时检查现有 VSSCI 插件  
 计划安装源代码管理插件的用户可能已经现有源代码管理插件安装在计算机上。 \(安装程序\) 安装程序的插件，您创建应确定是否存在相关的注册表项的现有值。 如果已设置这些注册表项，安装程序应该询问用户是否为默认的源代码管理插件注册您的插件，并替换已安装。  
  
## 错误结果代码和报告  
 `SCC_OK` 返回源控制功能的代码指示操作已成功的所有文件。 如果操作失败，则应返回遇到的最后一个错误代码。  
  
 用于报告的规则是，如果在 IDE 中发生错误，IDE 将负责来报告它。 如果错误发生在源代码管理系统，源代码管理插件负责来报告它。 例如，"当前选择任何文件"将报告通过 IDE 中，而"此文件已签出"将报告该插件。  
  
## 上下文结构  
 在调用 [SccInitialize](../extensibility/sccinitialize-function.md), ，调用方传递 `ppvContext` 参数，它是 void 未初始化句柄。 源代码管理插件可以忽略此参数或它可以分配任何种类的结构，并将指针传递指针放入到该结构。 IDE 不能理解此结构中，但它将指针传递给此结构到插件中的每个其他调用。 本文将提供给插件的有价值的上下文缓存信息可以使用仍然存在整个函数调用，而无需使用全局变量的全局状态信息进行维护。 此插件负责释放上调用的结构 [SccUninitialize](../extensibility/sccuninitialize-function.md)。  
  
 如果插件集 `SCC_CAP_REENTRANT` 中位 [SccInitialize](../extensibility/sccinitialize-function.md) \(具体而言，在 `lpSccCaps` 参数\)，多个上下文结构用来跟踪处于打开状态的所有项目。  
  
## Bitflags 和其他命令选项  
 对于每个命令，如 [SccGet](../extensibility/sccget-function.md), ，IDE 可以指定多个更改该命令的行为的选项。  
  
 在 API 支持的某些选项来通过 IDE 设置 `fOptions` 参数。 中描述了这些选项 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md) 以及它们影响的命令。 一般情况下，这些是为其不会提示用户的选项。  
  
 因为在源代码管理插件之间差别很大，这种方式，未定义最用户可配置的设置选项。 因此，建议使用的机制是 **高级** 按钮。 例如，在 **获取** 对话框中，则 IDE 将显示它了解，但它还显示的信息 **高级** 按钮如果插件具有用于此命令的选项。 当用户单击 **高级** 按钮，IDE 调用 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 启用源代码管理插件，以提示用户输入信息，如 bitflags 或日期\/时间。 该插件将返回此信息在一个结构，传递回期间 `SccGet` 命令。  
  
## 请参阅  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)   
 [创建了源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)