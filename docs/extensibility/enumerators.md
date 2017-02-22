---
title: "枚举器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件，枚举器"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 枚举器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本部分列出的源代码管理插件必须要知道源控制插件 API 中的枚举器数据类型。  
  
## 本节内容  
 [命令代码](../extensibility/command-code-enumerator.md)  
 枚举用于选项 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 和 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 函数。  
  
 [消息](../extensibility/message-enumerator.md)  
 枚举用于打印的回拨，标志 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
 [文件状态代码](../extensibility/file-status-code-enumerator.md)  
 包含已命名的常量值用于指定源代码管理下的文件的状态。  
  
 [目录状态代码](../extensibility/directory-status-code-enumerator.md)  
 包含已命名的常量值用于指定源代码管理下的目录的状态。  
  
## 相关章节  
 [创建了源代码管理插件](../extensibility/internals/creating-a-source-control-plug-in.md)  
 定义源控制插件 SDK 并介绍包含的资源。  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 提示用户提供对于给定的命令的高级选项。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 检查以了解其当前状态的文件的列表。 此外，使用 `pfnPopulate` 函数，当文件不匹配的条件时通知调用方 `nCommand`。  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述使用的回调函数 [SccOpenProject](../extensibility/sccopenproject-function.md) 来从源代码管理插件通过 IDE 显示消息。  
  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)  
 提供源控制插件 API 中的所有元素的完整列表。