---
title: "源控件插件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5169b3d74a77bbb079dab5b310a3b7ebbbeff0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-ins"></a>源控件插件
源控件插件 SDK 引用部分包含完整接口规范，支持使用源代码管理系统以与集成[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它指定的语法和语义到接口与源代码管理插件必须实现的各种函数和数据类型[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)。  
  
## <a name="in-this-section"></a>本节内容  
 [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)  
 列出必须由源代码管理插件为了遵守源控制插件 API 实现的函数。  
  
 [通过 IDE实现的回叫函数](../extensibility/callback-functions-implemented-by-the-ide.md)  
 描述源代码管理插件使用某些命令正在执行时将信息传递回 IDE 的函数。  
  
 [枚举器](../extensibility/enumerators.md)  
 列出源代码管理插件必须要知道源控件插件 API 中的枚举器数据类型。  
  
 [功能标志](../extensibility/capability-flags.md)  
 描述`SCC_CAP_xxx`标志，是指示提供程序的功能。  
  
 [特定命令使用的位标志](../extensibility/bitflags-used-by-specific-commands.md)  
 列出在特定命令的上下文中有用的标志。  
  
 [错误代码](../extensibility/error-codes.md)  
 列出了作为函数返回的常见错误值`SCCTRN`。  
  
 [作为用于查找源代码管理插件的密钥的字符串](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 描述用于访问注册表来查找源代码管理插件的项。  
  
 [MSSCCPRJ.SCC 文件](../extensibility/mssccprj-scc-file.md)  
 描述，其中包含信息不透明的 IDE 中，但用于通过源代码管理插件在版本控制中找到解决方案或项目的客户端文件。  
  
 [实现源代码管理插件的最佳做法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 提供要记住你要实现源控制插件 API 时的重要技术提醒的集合。  
  
 [字符串长度限制](../extensibility/restrictions-on-string-lengths.md)  
 描述在各种函数中使用的字符串的长度上的源控件插件 API 中的限制。  
  
 [术语表](../extensibility/source-control-plug-in-glossary.md)  
 提供有用的术语和用于读取的源控件插件 SDK 文档其定义。  
  
 [如何：关闭源代码管理插件的兼容性警告](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 描述如何禁用警告。  
  
## <a name="related-sections"></a>相关章节  
 [源控件插件示例](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 提供的源代码管理插件功能的示例。  
  
 [源代码管理插件的测试指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 介绍与源代码管理插件相关的测试过程。  
  
 [创建源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)  
 讨论如何创建了源代码管理插件，提供源代码管理功能，在使用时[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]源控制用户界面 (UI)。  
  
 [Visual Studio SDK 引用](../extensibility/visual-studio-sdk-reference.md)  
 显示一个列表的参考主题。