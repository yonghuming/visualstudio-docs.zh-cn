---
title: "FIELD_INFO | Microsoft Docs"
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
  - "FIELD_INFO"
helpviewer_keywords: 
  - "FIELD_INFO 结构"
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此结构描述一个局部变量、参数，或其他字段。  
  
## 语法  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## 成员  
 dwFields  
 标志的组合从指定的 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 枚举的哪些成员填充。  
  
 bstrFullName  
 字段的全名。  
  
 bstrName  
 字段的短名称。  
  
 bstrType  
 字段的类型。  
  
 dwModifiers  
 标志的组合。描述字段的 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 枚举的。  
  
## 备注  
 此结构传递给该方法的 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)