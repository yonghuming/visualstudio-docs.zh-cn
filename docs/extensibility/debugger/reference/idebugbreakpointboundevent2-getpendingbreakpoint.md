---
title: "IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointBoundEvent2::GetPendingBreakpoint"
helpviewer_keywords: 
  - "IDebugBreakpointBoundEvent2::GetPendingBreakpoint"
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBreakpointBoundEvent2::GetPendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取必须挂起的断点。  
  
## 语法  
  
```cpp#  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```cpp#  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### 参数  
 `ppPendingBP`  
 \[out\] 返回表示必须挂起的断点的 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 接口的 **CBreakpointSetDebugEventBase** 对象的方法。  
  
```cpp#  
STDMETHODIMP CBreakpointSetDebugEventBase::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2 **ppPendingBP)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppPendingBP )  
    {  
        if ( m_pPendingBP )  
        {  
            *ppPendingBP = m_pPendingBP;  
  
            m_pPendingBP->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## 请参阅  
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)