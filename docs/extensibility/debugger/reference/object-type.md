---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "OBJECT_TYPE 枚举"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定一个对象的类型从表达式计算器。  
  
## 语法  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## 成员  
 OBJECT\_TYPE\_BOOLEAN  
 指示对象布尔值。  
  
 OBJECT\_TYPE\_CHAR  
 指示该对象是字符。  
  
 OBJECT\_TYPE\_I1  
 指示该对象是一个字节带符号整数。  
  
 OBJECT\_TYPE\_U1  
 指示该对象是一个字节无符号整数。  
  
 OBJECT\_TYPE\_I2  
 指示该对象是一个双字节的符号整数。  
  
 OBJECT\_TYPE\_U2  
 指示该对象是双字节的无符号整数。  
  
 OBJECT\_TYPE\_I4  
 指示该对象是一个四个字节的符号整数。  
  
 OBJECT\_TYPE\_U4  
 指示该对象是四个字节的无符号整数。  
  
 OBJECT\_TYPE\_I8  
 指示该对象是八个字节带符号整数。  
  
 OBJECT\_TYPE\_U8  
 指示该对象是八个字节无符号整数。  
  
 OBJECT\_TYPE\_R4  
 指示该对象是一个四个字节的浮点数。  
  
 OBJECT\_TYPE\_R8  
 指示该对象是八个字节浮点数。  
  
 OBJECT\_TYPE\_OBJECT  
 指示该对象是对象。  
  
 OBJECT\_TYPE\_NULL  
 指示对象为空。  
  
 OBJECT\_TYPE\_CLASS  
 指示该对象是类。  
  
## 备注  
 将作为参数传递 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) 和 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) 方法。  
  
## 要求  
 标题:ee.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)