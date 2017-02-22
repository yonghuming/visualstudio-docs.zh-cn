---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在特定线程注意注意执行\) 的执行 \(或终止。  
  
## 语法  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### 参数  
 `pOriginatingProgram`  
 \[in\] 表示程序的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象步骤。  
  
 `dwTid`  
 \[in\] 指定线程的标识关注。  
  
 `fWatch`  
 \[in\] 非零 \(`TRUE`\) 表示开始监视由标识的线程的执行。 `dwTid`;否则，零 \(0\)`FALSE`\) 的含义停止监视 `dwTid`的执行。  
  
 `dwFrame`  
 \[in\] 指定控件的步骤类型的帧索引。  在这种值为零 \(0\) 时，步骤类型为 “步骤进入”，程序应停止，只要 `dwTid` 确定的线程上执行。  当 `dwFrame` 是非零时，步骤类型是 “step”，程序应停止，仅当 `dwTid` 确定的线程在索引小于 `dwFrame`是等于或高堆栈中的帧运行。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 在会议调试管理器 \(SDM\)步骤程序时，确定由 `pOriginatingProgram` 参数，则通过调用此方法以通知其他附加程序。  
  
 此方法只适用于与样线 \- 步骤。  
  
## 请参阅  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)