---
title: "IDebugStackFrame2::EnumProperties |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5359698b2ae148abd5fc38da346ebcd5c456634c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/06/2017

---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
创建与该堆栈帧，如本地变量关联的属性的枚举数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwFieldSpec`  
 [in]中的标志的组合[DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)指定哪些字段中枚举的枚举[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)结构是否填充的。  
  
 `nRadix`  
 [in]用于设置格式的任何数字信息基数。  
  
 `refiid`  
 [in]筛选器用于选择哪个选项卡的 GUID [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)结构是要枚举，如`guidFilterLocals`。  
  
 `dwTimeout`  
 [in]以毫秒为单位，从此方法返回前等待的最长时间。 使用`INFINITE`无限期等待。  
  
 `pcelt`  
 [out]返回的枚举的属性的数量。 这是调用相同[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)方法。  
  
 `ppEnum`  
 [out]返回[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)对象，其中包含所需的属性的列表。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法可以通过使用单个调用检索所有所选的属性，因为它是比按顺序调用快[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)和[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
