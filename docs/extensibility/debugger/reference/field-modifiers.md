---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "FIELD_MODIFIERS 枚举"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

为字段类型指定修饰符。  
  
## 语法  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## 成员  
 FIELD\_MOD\_ACCESS\_TYPE  
 指示字段无法访问。  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 指示字段具有公共访问权限。  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 指示字段保护访问。  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 指示字段访问私有。  
  
 FIELD\_MOD\_NOMODIFIERS  
 指示字段没有修饰符。  
  
 FIELD\_MOD\_STATIC  
 指示字段是静态的。  
  
 FIELD\_MOD\_CONSTANT  
 指示字段是常数。  
  
 FIELD\_MOD\_TRANSIENT  
 指示字段是瞬态的。  
  
 FIELD\_MOD\_VOLATILE  
 指示字段是可变的。  
  
 FIELD\_MOD\_ABSTRACT  
 指示字段是抽象的。  
  
 FIELD\_MOD\_NATIVE  
 指示字段是本机程序。  
  
 FIELD\_MOD\_SYNCHRONIZED  
 指示字段同步。  
  
 FIELD\_MOD\_VIRTUAL  
 指示字段是虚拟的。  
  
 FIELD\_MOD\_INTERFACE  
 指示字段是接口。  
  
 FIELD\_MOD\_FINAL  
 指示字段是致命的。  
  
 FIELD\_MOD\_SENTINEL  
 指示字段是接受零。  
  
 FIELD\_MOD\_INNERCLASS  
 指示字段是内部类。  
  
 FIELD\_TYPE\_OPTIONAL  
 指示字段是可选的。  
  
 FIELD\_MOD\_BYREF  
 指示字段是引用参数。  这是专用于为方法参数。  
  
 FIELD\_MOD\_HIDDEN  
 指示在另一个上下文需要隐藏或现有字段;例如， [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 静态局部。  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 指示字段将 `IUnknown` 接口表示形式。  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 指示字段具有指定特殊名称，例如，构造函数 \(仅[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]`.ctor` \)。  
  
 FIELD\_MOD\_HIDEBYSIG  
 指示字段具有 `Overloads` 关键字是否应用于它 \(仅[!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] \)。  
  
 FIELD\_MOD\_WRITEONLY  
 指示字段是只读。  ，因为单个的使用这样的只读字段是函数求值，此值在 `FIELD_MOD_ALL`不包括。  用户必须显式请求 `FIELD_MOD_WRITEONLY` 字段。  
  
 FIELD\_MOD\_ACCESS\_MASK  
 指示字段访问掩码。  
  
 FIELD\_MOD\_MASK  
 指示字段修饰符掩码。  
  
## 备注  
 用于 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) 结构的 `dwModifiers` 成员。  
  
 这些值还通过向筛选器的 [EnumFields](../Topic/IDebugContainerField::EnumFields.md) 方法定域的。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../Topic/IDebugContainerField::EnumFields.md)