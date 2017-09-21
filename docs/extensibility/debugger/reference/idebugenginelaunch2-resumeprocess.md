---
title: "IDebugEngineLaunch2::ResumeProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::ResumeProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::ResumeProcess"
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineLaunch2::ResumeProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

进程继续执行。  
  
## 语法  
  
```cpp#  
HRESULT ResumeProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int ResumeProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### 参数  
 `pProcess`  
 \[in\] 表示要还原的处理 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 备注  
 ，在处理生成了与 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 方法后，将调用此方法。  
  
## 请参阅  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)