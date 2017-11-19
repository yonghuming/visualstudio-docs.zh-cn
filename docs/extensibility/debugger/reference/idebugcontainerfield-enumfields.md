---
title: "IDebugContainerField::EnumFields |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugContainerField::EnumFields
helpviewer_keywords: IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e1eb67855ae1e13970ad5eab2eba8dd6308abbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
创建的容器的字段的枚举数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `dwKindFilter`  
 [in]组合[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)选择要枚举的字段的常量。 字段类型可以描述存储类型，例如类或基元，或特定的信息，如本地、 参数或"this"指针。  
  
 `dwModifiersFilter`  
 [in]组合[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)选择要枚举的字段的常量。 字段修饰符可以如公共或私有或存储信息，如虚拟、 静态的或最终的访问权限。  
  
 `pszNameFilter`  
 [in]要枚举的字段的名称。 如果要返回的所有字段，这可以是 null 值。  
  
 `nameMatch`  
 [in]取值范围为[NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)枚举，用于控制是否搜索是否区分大小写。  
  
 `ppEnum`  
 [out]返回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)表示的字段的列表对象。 如果没有字段，则返回 null 值。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK 或 S_FALSE 如果没有字段。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 `dwKindFilter`， `dwModifiersFilter`，和`pszNameFilter`参数可以结合使用，例如，若要选择名为"MyMethod"的所有公共虚拟方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)