---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
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
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "FIELD_INFO_FIELDS 枚举"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定检索的信息有关 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。  
  
## 语法  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## 成员  
 FIF\_FULLNAME  
 初始化\/使用在 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) 结构的 `bstrFullName` 字段。  
  
 FIF\_NAME  
 初始化\/使用在 `FIELD_INFO` 结构的 `bstrName` 字段。  
  
 FIF\_TYPE  
 初始化\/使用在 `FIELD_INFO` 结构的 `bstrType` 字段。  
  
 FIF\_MODIFIERS  
 初始化\/使用在 `FIELD_INFO` 结构的 `bstrModifiers` 字段。  
  
## 备注  
 这些值还通过，因为参数。 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法指定 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) 结构的哪些字段进行初始化。  
  
 这些值也用于 `FIELD_INFO` 结构的 `dwFields` 成员指示哪些字段是使用和有效。  
  
 这些标志可以按位组合使用 `OR`。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)