---
title: "DEBUG_ADDRESS_UNION |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_ADDRESS_UNION
helpviewer_keywords: DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7f2f01ee30949fc5b82f2bba868e433a4f3a14e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
描述不同类型的地址。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>术语  
 dwKind  
 取值范围为[ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)枚举，指定如何解释联合。  
  
 addr.addrNative  
 [C + +]包含[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)结构如果`dwKind`= ADDRESS_KIND_NATIVE。  
  
 addr.addrThisRel  
 [C + +]包含[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)结构如果`dwKind`= ADDRESS_KIND_UNMANAGED_THIS_RELATIVE。  
  
 addr.addUPhysical  
 [C + +]包含[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)结构如果`dwKind`= ADDRESS_KIND_UNMANAGED_PHYSICAL。  
  
 addr.addrMethod  
 [C + +]包含[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)结构如果`dwKind`= ADDRESS_KIND_METHOD。  
  
 addr.addrField  
 [C + +]包含[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)结构如果`dwKind`= ADDRESS_KIND_FIELD。  
  
 addr.addrLocal  
 [C + +]包含[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)结构如果`dwKind`= ADDRESS_KIND_LOCAL。  
  
 addr.addrParam  
 [C + +]包含[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)结构如果`dwKind`= ADDRESS_KIND_PARAM。  
  
 addr.addrArrayElem  
 [C + +]包含[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)结构如果`dwKind`= ADDRESS_KIND_ARRAYELEM。  
  
 addr.addrRetVal  
 [C + +]包含[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)结构如果`dwKind`= ADDRESS_KIND_RETVAL。  
  
 addr.unused  
 [C + +] 填充。  
  
 Addr  
 [C + +]联合的名称。  
  
 unionmember  
 [仅限 C#]此值需要封送到适当的结构类型基于`dwKind`。 有关之间的关联，请参见备注`dwKind`和联合的解释。  
  
## <a name="remarks"></a>备注  
 此结构是的一部分[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)结构和表示大量不同类型的地址之一 (`DEBUG_ADDRESS`结构通过调用填充[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法)。  
  
 [仅限 C#]下表显示如何解释`unionmember`的地址的每一类的成员。 该示例演示如何这样做是出于一种类型的地址。  
  
|`dwKind`|`unionmember`解释为|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>示例  
 此示例演示如何解释一种类型的地址 (`METADATA_ADDRESS_ARRAYELEM`) 的`DEBUG_ADDRESS_UNION`C# 中的结构。 可以在完全相同的方式解释剩余元素。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)