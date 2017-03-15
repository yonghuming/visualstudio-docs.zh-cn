---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在调试引擎 \(DE\)创建挂起的断点。  
  
## 语法  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### 参数  
 `pBPRequest`  
 \[in\] 描述挂起的断点创建的 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 对象。  
  
 `ppPendingBP`  
 \[out\] 返回表示挂起的断点的 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  通常返回 `E_FAIL` ，如果 `pBPRequest` 参数不匹配 DE 支持的任何语言，如果 `pBPRequest` 参数无效或不完整。  
  
## 备注  
 挂起断点实质上是所需的所有信息的集合绑定断点代码。  从此方法返回的挂起的断点将不一定代码，直到 [将绑定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 方法调用。  
  
 对于每个挂起的断点用户集，会议调试管理器 \(SDM\)对每个附加 DE 的此方法。  将由验证的、断点用于运行该 DE 的过程是有效的。  
  
 当用户将在某行代码中设置断点， DE 可以自由绑定断点到对应于此代码的文档的最接近的行。  这使得用户可以在一个多行语句的第一行中设置断点，但是，将其绑定在最后一行 \(其中所有代码在调试信息特性化\)。  
  
## 示例  
 下面的示例演示如何执行简单的 `CProgram` 对象的方法。  `IDebugEngine2::CreatePendingBreakpoint` 的 DE 的实现可以转发对的所有调用方法实现在每个程序中。  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## 请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [将绑定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)