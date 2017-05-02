---
title: "Windows 脚本主机 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows 脚本宿主, 实现宿主"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows 脚本主机
当实现 Microsoft Windows 脚本宿主时，可以安全地，假设一个脚本引擎只调用 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 接口在基础线程中，只要宿主执行以下操作：  
  
-   选择基本线程 \(通常包含消息循环\) 的线程。  
  
-   实例化在基本线程的脚本引擎。  
  
-   调用脚本引擎只有方法从基本线程，除此之外，其中明确允许，在 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 和 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)情况下。  
  
-   调用脚本引擎的仅安排对象从基本线程。  
  
-   确保消息循环在基础线程在运行，如果提供窗口句柄。  
  
-   确保仅在宿主的对象模型作为事件源的对象在基础线程。  
  
 这些规则可由所有单线程的宿主会自动执行。  中描述的该受限制的设计上面特意足够松散的允许宿主通过调用另一个线程的 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 中止一个承受不住的脚本 \(启动时 CTRL\+BREAK 处理程序或模拟\) 使用 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)，或\) 在新线程的脚本。  
  
## 备注  
 这些限制都不适用于选择实现一个自由线程的 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 接口和一个自由线程的对象模型的主机。  此宿主可以使用所有线程的 [IActiveScript](../winscript/reference/iactivescript.md) 接口，因此，不受限制。  
  
## 请参阅  
 [\<PAVE OVER\> Microsoft Windows 脚本接口 \- 介绍](http://msdn.microsoft.com/library/3d10169f-2984-49ef-90c6-dd89c97f1dd6)