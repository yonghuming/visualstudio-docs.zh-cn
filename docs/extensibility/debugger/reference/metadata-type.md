---
title: "METADATA_TYPE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 478cf0efe2bcb9079731ffd3154ce55352e35805
ms.lasthandoff: 02/22/2017

---
# <a name="metadatatype"></a>METADATA_TYPE
此结构指定字段类型从元数据中获取有关信息。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```c#  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>参数  
 ulAppDomainID  
 该符号所来自的应用程序 ID。 这用于唯一标识该应用程序的实例。  
  
 guidModule  
 包含此字段的模块的 GUID。  
  
 tokClass  
 此类型的元数据令牌 ID。  
  
 [C++]`_mdToken` is a `typedef` for a 32-bit `int`.  
  
## <a name="remarks"></a>备注  
 此结构中的联合的一部分显示[TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)结构时`dwKind`字段`TYPE_INFO`结构设置为`TYPE_KIND_METADATA`(取值范围为[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)枚举)。  
  
 `tokClass`值是唯一标识某个类型的元数据标记。 有关如何解释较高的一位的元数据标记 ID 的详细信息，请参阅`CorTokenType`corhdr.h 中的文件中枚举[!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)]SDK。  
  
## <a name="requirements"></a>要求  
 标头︰ sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
