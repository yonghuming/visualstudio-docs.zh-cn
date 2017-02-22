---
title: "TYPE_INFO | Microsoft Docs"
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
  - "TYPE_INFO"
helpviewer_keywords: 
  - "TYPE_INFO 结构"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构指定各种有关字段类型的信息。  
  
## 语法  
  
```cpp#  
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
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### 参数  
 dwKind  
 从确定如何解释该联合的 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 枚举的值。  
  
 type.typeMeta  
 只有 C\+\+ \[\] 包含一 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 结构，如果 `dwKind` 是 `TYPE_KIND_METADATA`。  
  
 type.typePdb  
 只有 C\+\+ \[\] 包含一 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 结构，如果 `dwKind` 是 `TYPE_KIND_PDB`。  
  
 type.typeBuilt  
 只有 C\+\+ \[\] 包含一 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) 结构，如果 `dwKind` 是 `TYPE_KIND_BUILT`。  
  
 type.unused  
 未使用的空白。  
  
 type  
 联合的名称。  
  
 unionmember  
 \[仅限于 c\#\] 使此根据 `dwKind`的相应 framework 类型。  
  
## 备注  
 此结构传递给该方法的 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 方法。  结构的内容如何解释基于 `dwKind` 字段。  
  
> [!NOTE]
>  只有 C\+\+ \[\]，如果 `dwKind` 等于 `TYPE_KIND_BUILT`，然后释放基础 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象是必要的，因为销毁 `TYPE_INFO` framework 的访问。  这是通过调用 `typeInfo.type.typeBuilt.pUnderlyingField->Release()`完成。  
  
 \[仅限于 c\#\] 下表显示如何解释每 `unionmember` 成员类型。  示例显示了如何为一种类型执行。  
  
|`dwKind`|解释了`unionmember`|  
|--------------|----------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## 示例  
 此示例演示如何解释 `TYPE_INFO` 结构的 `unionmember` 成员在 C\# 中。  此示例仅显示介绍了一种类型 \(`TYPE_KIND_METADATA`\)，但其他类似地介绍。  
  
```c#  
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
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)