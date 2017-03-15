---
title: "IDebugBreakpointRequest2::GetLocationType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest2::GetLocationType"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2::GetLocationType"
ms.assetid: b6d14c59-d3aa-48ff-8278-f6b5bba9c2f3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBreakpointRequest2::GetLocationType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取该断点请求的断点位置类型。  
  
## 语法  
  
```cpp#  
HRESULT GetLocationType(   
   BP_LOCATION_TYPE* pBPLocationType  
);  
```  
  
```c#  
int GetLocationType(   
   out enum_BP_LOCATION_TYPE pBPLocationType  
);  
```  
  
#### 参数  
 `pBPLocationType`  
 \[out\] 返回从描述该断点请求的位置的 [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) 枚举的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  ，如果在关联的 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 结构的 `bpLocation` 字段无效，则返回 `E_FAIL` 。  
  
## 示例  
 下面的示例演示如何执行显示[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 接口的简单 `CDebugBreakpointRequest` 对象的方法。  
  
```  
HRESULT CDebugBreakpointRequest::GetLocationType(BP_LOCATION_TYPE* pBPLocationType)    
{    
   HRESULT hr;    
  
   if (pBPLocationType)    
   {    
      // Set default BP_LOCATION_TYPE.    
      *pBPLocationType = BPLT_NONE;    
  
      // Check if the BPREQI_BPLOCATION flag is set in BPREQI_FIELDS.    
      if (IsFlagSet(m_bpRequestInfo.dwFields, BPREQI_BPLOCATION))    
      {    
         // Get the new BP_LOCATION_TYPE.    
         *pBPLocationType = m_bpRequestInfo.bpLocation.bpLocationType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## 请参阅  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)