---
title: "dwTYPE_KIND | Microsoft Docs"
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
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "dwTYPE_KIND 枚举"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定如何解释 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象的类型。  
  
## 语法  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### 参数  
 TYPE\_KIND\_METADATA  
 应当解释 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) 联合用作 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 结构。  
  
 TYPE\_KIND\_PDB  
 应当解释 `TYPE_INFO` 联合用作 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 结构。  
  
 TYPE\_KIND\_BUILT  
 应当解释 `TYPE_INFO` 联合用作 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) 结构。  
  
## 备注  
 此枚举的值。 `dwKind` 显示 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) 结构字段和使用确定如何解释 `type` 联合的成员。  `TYPE_INFO` framework 通过对 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) 方法的调用返回。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)