---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

已弃用。  不要使用。  
  
## 语法  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### 参数  
 `pMDMProgram`  
 \[in\] 表示程序附加 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口。  
  
 `pCallback`  
 \[in\] 要使用的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 接口发送调试事件对 SDM。  
  
 `dwReason`  
 \[in\] 从用于附加指定其原因的 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) 枚举的值。  
  
## 返回值  
 实现应始终返回 `E_NOTIMPL`。  
  
## 备注  
  
> [!WARNING]
>  自 [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]，不再使用此方法应始终返回 `E_NOTIMPL`。  请参见一种替代方法的 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 接口，如果程序节点需要指示则无法附加到或，如果程序节点集程序 `GUID`。 否则，请执行 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 方法。  
  
## 在 Visual Studio 2005 中前面  
 ，仅当、正在调试，的程序的地址空间中运行此方法需要执行。  否则，此方法应返回 `S_FALSE`。  
  
 当调用此方法时， DE 必须发送 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) 事件对象，则为; 如果没有为 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 接口的此实例已经发送，以及 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 和 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 事件对象。  [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 事件对象，如果 `dwReason` 参数是 `ATTACH_REASON_LAUNCH`，然后发送。  
  
 DE 在实例数据必须对 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件对象提供的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象的 [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 方法，并且必须存储过程的 GUID。 DE 实现的 `IDebugProgram2` 对象。  
  
## 请参阅  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)