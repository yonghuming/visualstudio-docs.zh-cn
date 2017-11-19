---
title: "IDebugProperty2::EnumChildren |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::EnumChildren
helpviewer_keywords: IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 82f08fad921a2249e6a7943acec1fb9cb60e006b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
检索属性的子级的列表。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>参数  
 `dwFields`  
 [in]中的标志的组合[DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)指定哪些字段中枚举的枚举[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)结构是否填充的。  
  
 `dwRadix`  
 [in]指定用于格式化数值的任何信息的基数。  
  
 `guidFilter`  
 [in]使用与筛选器的 GUID`dwAttribFilter`和`pszNameFilter`参数从中选择`DEBUG_PROPERTY_INFO`子级都要进行枚举。 例如，`guidFilterLocals`本地变量的筛选器。  
  
 `dwAttribFilter`  
 [in]中的标志的组合[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)指定哪种类型的对象，若要枚举，例如枚举`DBG_ATTRIB_METHOD`对于可能是此属性的子级的所有方法。 与结合使用`guidFilter`和`pszNameFilter`参数。  
  
 `pszNameFilter`  
 [in]用于筛选器的名称`guidFilter`和`dwAttribFilter`参数从中选择`DEBUG_PROPERTY_INFO`子级都要进行枚举。 例如，将此参数设置为"MyX"筛选器，为所有子项具有名称"MyX。"  
  
 `dwTimeout`  
 [in]指定以毫秒为单位，从此方法返回前等待的最长时间。 使用`INFINITE`无限期等待。  
  
 `ppEnum`  
 [out]返回[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)对象，其中包含子属性的列表。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)