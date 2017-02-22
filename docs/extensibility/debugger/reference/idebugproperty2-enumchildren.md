---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
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
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索属性的子元素的列表。  
  
## 语法  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### 参数  
 `dwFields`  
 \[in\] 标志的组合从指定的 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 枚举在枚举的 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 结构的哪些字段将填充。  
  
 `dwRadix`  
 \[in\] 指定用于为所有数字信息基数。  
  
 `guidFilter`  
 \[in\] 筛选器的 GUID 用于以 `DEBUG_PROPERTY_INFO` 子项将枚举 `dwAttribFilter` 和 `pszNameFilter` 参数选择。  例如，局部变量的 `guidFilterLocals` 筛选器。  
  
 `dwAttribFilter`  
 \[in\] 标志的组合从指定的 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 枚举的枚举的哪些类型的对象，例如可能是此属性的子级的所有方法的 `DBG_ATTRIB_METHOD` 。  使用 `guidFilter` 和 `pszNameFilter` 参数的组合。  
  
 `pszNameFilter`  
 \[in\] 筛选器的名称用于以 `DEBUG_PROPERTY_INFO` 子项将枚举 `guidFilter` 和 `dwAttribFilter` 参数选择。  例如，将此参数设置为 “所有子级的 MyX”筛选器具有名称 “MyX”。  
  
 `dwTimeout`  
 \[in\] 以毫秒为单位指定最长时间，因此，在返回等待来自此方法。  使用 `INFINITE` 会无限期地等待。  
  
 `ppEnum`  
 \[out\] 返回包含子属性的列表 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)