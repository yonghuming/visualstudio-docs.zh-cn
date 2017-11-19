---
title: "TYPE_INFO |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TYPE_INFO
helpviewer_keywords: TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dc77aa5b633c4160fc34717c0b9382d89d9f0e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="typeinfo"></a>TYPE_INFO
此结构指定各种类型的字段的类型有关的信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>参数  
 dwKind  
 取值范围为[dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)确定如何解释联合的枚举。  
  
 type.typeMeta  
 [C + +]包含[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)结构如果`dwKind`是`TYPE_KIND_METADATA`。  
  
 type.typePdb  
 [C + +]包含[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)结构如果`dwKind`是`TYPE_KIND_PDB`。  
  
 type.typeBuilt  
 [C + +]包含[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)结构如果`dwKind`是`TYPE_KIND_BUILT`。  
  
 type.unused  
 未使用的填充。  
  
 类型  
 联合的名称。  
  
 unionmember  
 [仅限 C#]封送到合适的结构类型基于`dwKind`。  
  
## <a name="remarks"></a>备注  
 此结构传递给[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)方法中填充位置。 如何解释结构的内容取决于`dwKind`字段。  
  
> [!NOTE]
>  [C + +]如果`dwKind`等于`TYPE_KIND_BUILT`，则有必要释放基础[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)对象时销毁`TYPE_INFO`结构。 可以通过调用 `typeInfo.type.typeBuilt.pUnderlyingField->Release()` 来完成此操作。  
  
 [仅限 C#]下表显示如何解释`unionmember`针对每种类型的成员。 该示例演示如何这样做是出于一种类型的类型。  
  
|`dwKind`|`unionmember`解释为|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>示例  
 此示例演示如何解释`unionmember`的成员`TYPE_INFO`C# 中的结构。 此示例演示解释的一种类型 (`TYPE_KIND_METADATA`) 但其他解释方式完全相同。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>要求  
 标头： sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)