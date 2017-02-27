---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "DEBUG_ADDRESS_UNION 联合"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述不同类型的地址。  
  
## 语法  
  
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
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## 术语  
 dwKind  
 从 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) 枚举中的一个值，该值指定如何解释联合。  
  
 addr.addrNative  
 只有 C\+\+ \[\] 包含 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_NATIVE。  
  
 addr.addrThisRel  
 只有 C\+\+ \[\] 包含[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE。  
  
 addr.addUPhysical  
 只有 C\+\+ \[\] 包含[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL。  
  
 addr.addrMethod  
 只有 C\+\+ \[\] 包含[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_METHOD。  
  
 addr.addrField  
 只有 C\+\+ \[\] 包含[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_FIELD。  
  
 addr.addrLocal  
 只有 C\+\+ \[\] 包含[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_LOCAL。  
  
 addr.addrParam  
 只有 C\+\+ \[\] 包含[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_PARAM。  
  
 addr.addrArrayElem  
 只有 C\+\+ \[\] 包含[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_ARRAYELEM。  
  
 addr.addrRetVal  
 只有 C\+\+ \[\] 包含[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 结构，如果 `dwKind` \= ADDRESS\_KIND\_RETVAL。  
  
 addr.unused  
 只有 C\+\+ \[\] 空白。  
  
 地址  
 只有 C\+\+ \[\] 联合的名称。  
  
 unionmember  
 \[仅限于 c\#\] 此值需要封送到基于 `dwKind`的相应 framework 类型。  有关该联合的 `dwKind` 和解释之间的关联参见备注。  
  
## 备注  
 此结构是 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) framework 的一部分并表示许多不同的某个地址 \( `DEBUG_ADDRESS` framework 通过对 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 方法的调用填充\)。  
  
 \[仅限于 c\#\] 下表显示如何解释每 `unionmember` 成员的地址。  示例显示了如何为一个地址执行。  
  
|`dwKind`|解释了`unionmember`|  
|--------------|----------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## 示例  
 此示例演示如何解释一地址 \(`METADATA_ADDRESS_ARRAYELEM`\) 在 C\# 中 `DEBUG_ADDRESS_UNION` 结构。  其余元素可能类似地介绍。  
  
```c#  
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
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)