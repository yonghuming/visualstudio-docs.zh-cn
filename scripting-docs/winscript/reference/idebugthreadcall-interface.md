---
title: "IDebugThreadCall 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall 接口"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall 接口
`IDebugThreadCall` 接口由使线程间调用与排列实现的 `IDebugThread` 提供由进程调试管理器\(PDM\)的元素通常实现。  
  
 PDM对所需线程的 `IDebugThreadCall` 接口，并且，`IDebugThreadCall` 接口计划调用这次期望实现。  `IDebugThreadCall` 接口将参数传递的参数信息。适当的顶部。  
  
 `IDebugThreadCall` 接口是一个自由线程的对象。  
  
## 方法  
 除了从 `IUnknown` 继承的方法之外，`IDebugThreadCall` 接口还公开下面的方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|处理调用运行在另一个线程的代码。|