---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

附加调试引擎 \(DE\)会过程或过程。  ，当 DE 运行定向到 SDM 时，调用该会话调试管理器 \(SDM\)。  
  
## 语法  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### 参数  
 `pProgram`  
 \[in\] 数组中表示要附加的程序的 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象。  这些是端口程序。  
  
 `rgpProgramNodes`  
 \[in\] 数组表示程序节点的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象，则每个程序中。  该数组的过程节点表示程序与在 `pProgram`。  给出程序节点，以使 DE 可以识别程序附加。  
  
 `celtPrograms`  
 \[in\] 程序和程序节点数。 `pProgram` 和 `rgpProgramNodes` 数组。  
  
 `pCallback`  
 \[in\] 要使用的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象发送调试事件对 SDM。  
  
 `dwReason`  
 \[in\] 从可连接这些过程指定其原因的 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) 枚举的值。  有关更多信息，请参见“备注”一节。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 连有三个影响程序，如下所示:  
  
-   `ATTACH_REASON_LAUNCH` 指示 DE 附加到程序，因为用户可以启动了包含它的过程。  
  
-   `ATTACH_REASON_USER` 指示用户显式请求、附加到程序 \(或包含一个程序\) 的过程。  
  
-   `ATTACH_REASON_AUTO` 指示 DE 附加到特定过程，因为它已经调试在特定的其他程序处理。  这也称为自动附加。  
  
 当调用此方法时， DE 需要按顺序发送以下事件:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) \(如果它尚未为调试引擎的特定实例已发送\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 此外，在中，如果附加的原因是 `ATTACH_REASON_LAUNCH`， DE 需要发送 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 事件。  
  
 对于 DE 获取 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象与正在调试的程序相对应，它可用于任何私有接口中查询。  
  
 在调用一个过程节点的方法之前在 `pProgram` 或 `rgpProgramNodes`给定的数组，在表示程序节点的 `IDebugProgram2` 接口都应，如果需要，启用模拟。  通常，但是，此步骤不是必需的。  有关更多信息，请参见 [安全问题](../../../extensibility/debugger/security-issues.md)。  
  
## 请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)