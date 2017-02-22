---
title: "BUILT_TYPE | Microsoft Docs"
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
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "BUILT_TYPE 结构"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构指定有关从元数据中获取的字段类型的信息。  
  
## 语法  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### 参数  
 ulAppDomainID  
 符号来自应用程序的 ID。  用于唯一标识应用程序的实例。  
  
 guidModule  
 包含此域模块的 GUID。  
  
 pUnderlyingField  
 标识基础字段的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象与此生成的字段。  
  
## 备注  
 此结构显示为 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) 结构的联合一部分，当 `TYPE_INFO` 结构的 `dwKind` 字段设置为 `TYPE_KIND_BUILT` 时 \(从 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 枚举的值\)。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)