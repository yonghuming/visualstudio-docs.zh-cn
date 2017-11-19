---
title: "实现源代码管理插件的最佳实践 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9099d652012fb8b45b7b79f9c620f4102e7af602
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>实现源代码管理插件的最佳做法
以下技术详细信息可帮助你可靠地实现了源代码管理插件中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="memory-management-issues"></a>内存管理问题  
 在大多数情况下，集成的开发环境 (IDE)，这是调用方，释放并分配内存。 源代码管理插件返回调用方分配的缓冲区中字符串和其他项。 它们发生的特定函数的说明中注明了异常。  
  
## <a name="arrays-of-file-names"></a>文件名称的数组  
 当传递的文件数组时，它将不传递为连续的文件名称数组。 它作为传递一个指针数组给文件的名称。 例如，在[SccGet](../extensibility/sccget-function.md)，通过传递文件名称`lpFileNames`参数，其中`lpFileNames`是实际指向的指针`char **`。 `lpFileNames`[0] 是指向第一个名称， `lpFileNames`[1] 是指向第二个名称，依次类推。  
  
## <a name="large-model"></a>大的模型  
 所有指针都是 32 位，即使在 16 位操作系统上。  
  
## <a name="fully-qualified-paths"></a>完全限定的路径  
 其中文件名或目录指定为参数，它们必须完全限定的路径或 UNC 路径，而无需结束反斜杠。 它负责的源代码管理插件转换到如果，它是基础的源控制系统的要求的相对路径。  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>指定完全限定的路径中的已注册 dll  
 IDE 无法再从相对路径 (例如，.\NewProvider.dll) 加载 Dll。 （例如 C:\Providers\NewProvider.dll），必须指定 DLL 的完整路径。 此要求可在 IDE 的安全增强通过阻止未经授权或模拟源控件 Dll 的加载。  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>安装你的源代码管理插件时检查现有 VSSCI 插件  
 计划安装你的源代码管理插件的用户可能已存在现有源代码管理插件安装在计算机上。 安装 （安装程序） 程序的插件，你创建应确定是否有相关的注册表项的现有值。 如果已设置这些密钥，安装程序应该询问用户是否为默认源代码管理插件注册插件，并替换已安装。  
  
## <a name="error-result-codes-and-reporting"></a>错误结果代码和报告  
 `SCC_OK`返回的源控件函数代码指示操作已成功为所有文件。 如果操作失败，它应返回遇到的最后一个错误代码。  
  
 用于报告的规则是，如果在 IDE 中发生错误，IDE 将负责来报告它。 如果源代码管理系统中发生错误，源代码管理插件负责来报告它。 例如，"当前选择任何文件"将报告由 IDE，而"此文件已签出"将报告由该插件。  
  
## <a name="the-context-structure"></a>上下文结构  
 在调用期间[SccInitialize](../extensibility/sccinitialize-function.md)，调用方传递`ppvContext`参数，它是 void 未经初始化即句柄。 源代码管理插件可以忽略此参数，或它可以分配任何类型的结构，并将向该结构的指针放入传递的指针。 IDE 不了解此结构，但它将指针传递给此结构到插件中的每个其他调用。 这将提供有价值的上下文缓存信息的插件，它可用于维护仍然存在整个函数调用，而无需使用全局变量的全局状态信息。 插件是负责释放上调用的结构[SccUninitialize](../extensibility/sccuninitialize-function.md)。  
  
 如果插件集`SCC_CAP_REENTRANT`中位[SccInitialize](../extensibility/sccinitialize-function.md) (具体而言，在`lpSccCaps`参数)，多个上下文结构用于跟踪处于打开状态的所有项目。  
  
## <a name="bitflags-and-other-command-options"></a>Bitflags 和其他命令选项  
 对于每个命令，如[SccGet](../extensibility/sccget-function.md)，IDE 可以指定多个更改命令的行为的选项。  
  
 该 API 支持的某些选项来通过 IDE 设置`fOptions`参数。 介绍了这些选项[Bitflags 使用特定命令](../extensibility/bitflags-used-by-specific-commands.md)以及这些设置会影响的命令。 一般情况下，这些是为其不会提示用户的选项。  
  
 这种方式，未定义最用户可配置的设置选项，因为它们广泛有所不同源控件插件。因此，建议的机制是**高级**按钮。 例如，在**获取**对话框中，则 IDE 将显示它了解，但它还显示的信息**高级**按钮如果插件都有为此命令的选项。 当用户单击**高级**按钮，IDE 调用[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)启用源代码管理插件以提示用户输入信息，如 bitflags 或日期/时间。 该插件在恢复期间传递的结构中返回此信息`SccGet`命令。  
  
## <a name="see-also"></a>另请参阅  
 [源控件插件](../extensibility/source-control-plug-ins.md)   
 [创建源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)