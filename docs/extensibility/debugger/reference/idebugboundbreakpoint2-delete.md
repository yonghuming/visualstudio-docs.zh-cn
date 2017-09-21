---
title: "IDebugBoundBreakpoint2::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::Delete"
helpviewer_keywords: 
  - "Delete 方法"
  - "IDebugBoundBreakpoint2::Delete 方法"
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBoundBreakpoint2::Delete
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

删除断点。  
  
## 语法  
  
```cpp#  
HRESULT Delete(   
   void   
);  
```  
  
```c#  
int Delete();  
```  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  返回 `E_BP_DELETED` ，如果绑定断点对象的状态设置为 `BPS_DELETED` \(的一部分 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) 枚举\)。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 接口的简单 `CBoundBreakpoint` 对象的方法。  
  
```  
HRESULT CBoundBreakpoint::Delete(void)    
{    
   HRESULT hr;    
  
   // Verify that the bound breakpoint has not been   
   // deleted. If deleted, then return hr = E_BP_DELETED.    
   if (m_state != BPS_DELETED)    
   {    
      m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);    
  
      // Change the state of the breakpoint to BPS_DELETED.    
      m_state = BPS_DELETED;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}     
```  
  
## 请参阅  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)