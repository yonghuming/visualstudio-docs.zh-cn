---
title: "源代码管理插件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件引用"
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 源代码管理插件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

源控制插件 SDK 参考部分包含的启用源代码管理系统集成在一起的完整接口规范 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 它指定的语法和源代码管理插件必须实现接口使用的各种函数和数据类型的语义 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成的开发环境 \(IDE\)。  
  
## 本节内容  
 [源代码管理插件 API 功能](../extensibility/source-control-plug-in-api-functions.md)  
 列出必须由源代码管理插件以便符合源控制插件 API 实现的函数。  
  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)  
 描述了源代码管理插件使用某些命令执行时将信息传递回 IDE 的函数。  
  
 [枚举器](../extensibility/enumerators.md)  
 列出在源代码管理插件必须要知道源控制插件 API 中的枚举器数据类型。  
  
 [功能标志](../extensibility/capability-flags.md)  
 描述 `SCC_CAP_xxx` 是指示提供程序的功能的标志。  
  
 [Bitflags 由特定的命令使用](../extensibility/bitflags-used-by-specific-commands.md)  
 列出在特定命令的上下文中有用的标志。  
  
 [错误代码](../extensibility/error-codes.md)  
 列出了常见的错误值作为函数所返回的 `SCCTRN`。  
  
 [字符串用作键用于查找源代码管理插件](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 介绍用于访问注册表，以查找源代码管理插件的快捷键。  
  
 [MSSCCPRJ。源代码管理文件](../extensibility/mssccprj-scc-file.md)  
 描述包含信息不透明的 IDE 中，但用于由源代码管理插件在版本控制中找到的解决方案或项目的客户端的文件。  
  
 [实现了源代码管理插件的最佳做法](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 提供重要的技术提醒记住虽然您要实现源控制插件 API 的集合。  
  
 [字符串长度限制](../extensibility/restrictions-on-string-lengths.md)  
 描述了有关各个函数中使用的字符串长度的源控制插件 API 中的限制。  
  
 [词汇表](../extensibility/source-control-plug-in-glossary.md)  
 提供了有用的术语和它们的定义来读取源控制插件 SDK 文档。  
  
 [如何: 关闭源代码管理插件的兼容性警告](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 描述如何禁用警告。  
  
## 相关章节  
 [Source Control Plug\-in Sample](http://msdn.microsoft.com/zh-cn/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 提供了源代码管理插件功能的示例。  
  
 [源代码管理插件的测试指南](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 介绍与源代码管理插件相关的测试过程。  
  
 [创建了源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)  
 讨论如何创建一个源代码管理插件，用于提供源代码管理功能，在使用时 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 源代码管理用户界面 \(UI\)。  
  
 [Visual Studio SDK 参考](../extensibility/visual-studio-sdk-reference.md)  
 显示一个列表的参考主题。