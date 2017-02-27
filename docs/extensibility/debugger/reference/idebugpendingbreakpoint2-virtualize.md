---
title: "IDebugPendingBreakpoint2::Virtualize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Virtualize"
helpviewer_keywords: 
  - "虚拟化方法"
  - "IDebugPendingBreakpoint2::Virtualize 方法"
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

切换此挂起的断点有效状态。  当挂起的断点有效，调试引擎会尝试将其绑定，新代码时加载到程序。  
  
## 语法  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### 参数  
 `fVirtualize`  
 \[in\] 设置为非零 \(`TRUE`\) 活动挂起的断点或零 \(`FALSE`\) 关闭虚拟化。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  ，如果断点删除，返回 `E_BP_DELETED` 。  
  
## 备注  
 有效的断点必须每次加载代码。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 接口的简单 `CPendingBreakpoint` 对象的方法。  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
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
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)