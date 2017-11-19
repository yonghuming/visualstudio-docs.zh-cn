---
title: "BUILT_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BUILT_TYPE
helpviewer_keywords: BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd8536f48d2204d79398000cb8503d7e03191af8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="builttype"></a>BUILT_TYPE
此结构指定字段类型从元数据中获取有关的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>参数  
 ulAppDomainID  
 符号源于应用程序 ID。 这用于唯一标识应用程序的实例。  
  
 guidModule  
 包含此字段的模块的 GUID。  
  
 pUnderlyingField  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)标识与此内置字段相关的基础字段的对象。  
  
## <a name="remarks"></a>备注  
 此结构显示为中的联合的一部分[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)结构时`dwKind`字段`TYPE_INFO`结构设置为`TYPE_KIND_BUILT`(从值[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)枚举）。  
  
## <a name="requirements"></a>要求  
 标头： sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)