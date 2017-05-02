---
title: "IDebugSyncOperation 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSyncOperation 接口"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation 接口
在特定时允许脚本引擎提取该操作\(例如表达式计算\)需要执行，如果嵌套阻塞线程。  接口提供取消无响应的操作还提供一个框架。  
  
 除了从 `IUnknown` 继承的方法之外，`IDebugSyncOperation` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|返回此同步操作的目标应用程序线程。|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|同步执行操作并返回。|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|取消操作正在进行中的另一个线程。|