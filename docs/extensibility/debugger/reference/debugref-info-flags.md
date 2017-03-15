---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "DEBUGREF_INFO_FLAGS 枚举"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定检索的信息有关调试引用对象。  
  
## 语法  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## 成员  
 DEBUGREF\_INFO\_NAME  
 初始化\/使用结构中的 `bstrName` 字段。  
  
 DEBUGREF\_INFO\_TYPE  
 初始化\/使用结构中的 `bstrType` 字段。  
  
 DEBUGREF\_INFO\_VALUE  
 初始化\/使用结构中的 `bstrValue` 字段。  
  
 DEBUGREF\_INFO\_ATTRIB  
 初始化\/使用结构中的`dwAttrib` 字段。  
  
 DEBUGREF\_INFO\_REFTYPE  
 初始化\/使用结构中的 `dwRefType` 字段。  
  
 DEBUGREF\_INFO\_REF  
 初始化\/使用结构中的 `pReference` 字段。  
  
 DEBUGREF\_INFO\_VALUE\_AUTOEXPAND  
 值字段应包含自动展开的值，如果有，则此类型的对象。  
  
 DEBUGREF\_INFO\_NONE  
 指示未设置任何标志。  
  
 DEBUGREF\_INFO\_ALL  
 指示标志掩码。  
  
## 备注  
 这些标志传递给 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) 和 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 方法指示 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 结构的哪些字段进行初始化。  
  
 用于 `DEBUG_REFERENCE_INFO` 结构的 `dwFields` 成员指示哪些字段是使用和有效，当结构返回。  
  
 这些值可能按位组合使用 `OR`。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)