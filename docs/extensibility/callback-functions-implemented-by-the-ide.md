---
title: "由 IDE 实现的回调函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理插件，回调函数"
  - "回调函数，源代码管理插件"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 由 IDE 实现的回调函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

要使与的集成为尽可能，并提供了统一的最终用户体验，无缝集成的开发环境 \(IDE\) 源代码管理插件可以使用 ide 实现的回调函数。 该插件可调用这些函数在源代码管理操作将信息传递到 IDE; 在适当的时间IDE 然后可以显示此信息作为其本机用户界面中的嵌入元素。 用户可以在此方案中比如果该插件使用自己的 UI 的占有率的体验。  
  
 必需的标头文件是 scc.h。 默认位置为 \\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\。 它也是在 VSIP 文件夹处都有源控制插件示例 \\Program Files\\VSIP 8.0\\MSSCCI\\。  
  
## 本节内容  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述使用的回调函数 [SccOpenProject](../extensibility/sccopenproject-function.md) 来从源代码管理插件通过 IDE 显示消息。  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 描述使用的回调函数 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE 不具有完全访问权限仅适用于的源代码管理插件，如版本控制下的文件的完整列表的信息。  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 描述使用的回调函数 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 操作。  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 描述使用的回调函数 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 操作。  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 介绍设置通过调用的回调函数 [SccSetOption](../extensibility/sccsetoption-function.md) 启用源代码管理插件通信名称变回 IDE。  
  
## 相关章节  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 打开一个项目。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 检查以了解其当前状态的文件的列表。 此外，使用 `pfnPopulate` 函数，当文件不匹配的条件时通知调用方 `nCommand`。  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 检查目录和一个项目或项目受源代码管理中的文件的列表。 找到每个目录和文件名称传递给回调函数。  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 检查名称的文件的列表对所做的更改。 每个文件的名称传递给回调函数以及将其更改状态。  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 设置各种选项。 每个选项开头 `SCC_OPT_xxx` 并具有其自己定义的值集。  
  
 [源代码管理插件](../extensibility/source-control-plug-ins.md)  
 描述源控件插件 SDK 的参考部分的内容。