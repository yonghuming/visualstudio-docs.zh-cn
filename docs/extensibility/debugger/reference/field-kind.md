---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "FIELD_KIND 枚举"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定在 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象的字段包含的。  
  
## 语法  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## 成员  
 FIELD\_KIND\_TYPE  
 指示字段仅类型。  
  
 FIELD\_KIND\_SYMBOL  
 指示字段是一个符号，与类型，名称和其他信息。  
  
 FIELD\_TYPE\_PRIMITIVE  
 指示字段是基元数据类型。  
  
 FIELD\_TYPE\_STRUCT  
 指示字段是结构。  
  
 FIELD\_TYPE\_CLASS  
 指示字段是类。  
  
 FIELD\_TYPE\_INTERFACE  
 指示字段是接口。  
  
 FIELD\_TYPE\_UNION  
 指示字段是联合。  
  
 FIELD\_TYPE\_ARRAY  
 指示字段是数组。  
  
 FIELD\_TYPE\_METHOD  
 指示字段是方法。  
  
 FIELD\_TYPE\_BLOCK  
 指示字段被阻止。  
  
 FIELD\_TYPE\_POINTER  
 指示字段是指针。  
  
 FIELD\_TYPE\_ENUM  
 指示字段是一个枚举数据类型。  
  
 FIELD\_TYPE\_LABEL  
 指示字段是一个标签。  
  
 FIELD\_TYPE\_TYPEDEF  
 指示字段是 typedef。  
  
 FIELD\_TYPE\_BITFIELD  
 指示字段是 bitfield。  
  
 FIELD\_TYPE\_NAMESPACE  
 指示字段是命名空间。  
  
 FIELD\_TYPE\_MODULE  
 指示字段是模块。  
  
 FIELD\_TYPE\_DYNAMIC  
 指示字段是动态的。  
  
 FIELD\_TYPE\_PROP  
 指示字段是属性。  
  
 FIELD\_TYPE\_INNERCLASS  
 指示字段是内部类。  
  
 FIELD\_TYPE\_REFERENCE  
 指示字段是引用。  
  
 FIELD\_TYPE\_EXTENDED  
 保留供将来使用。  
  
 FIELD\_SYM\_MEMBER  
 指示字段是的成员。  
  
 FIELD\_SYM\_LOCAL  
 指示字段本地。  
  
 FIELD\_SYM\_PARAMETER  
 指示字段是参数。  
  
 FIELD\_SYM\_THIS  
 指示字段是 “this”指针。  
  
 FIELD\_SYM\_GLOBAL  
 指示字段是全局的。  
  
 FIELD\_SYM\_PROP\_GETTER  
 指示字段检索属性。  
  
 FIELD\_SYM\_PROP\_SETTER  
 指示字段设置属性。  
  
 FIELD\_SYM\_EXTENDED  
 保留供将来使用。  
  
 FIELD\_KIND\_MASK  
 指示字段类型的掩码。  
  
 FIELD\_TYPE\_MASK  
 指示字段类型的掩码。  
  
 FIELD\_SYM\_MASK  
 指示掩码对于符号信息。  
  
## 备注  
 调用返回到 [GetKind](../Topic/IDebugField::GetKind.md) 方法。  
  
 基于该字段， [QueryInterface](/visual-cpp/atl/queryinterface) 可以按接口的一个更具体的窗体的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口。  例如，因此，如果 [GetKind](../Topic/IDebugField::GetKind.md) 返回 `FIELD_TYPE_METHOD`然后，可以调用 `QueryInterface` 我`DebugField` 获取 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 接口。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../Topic/IDebugField::GetKind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)