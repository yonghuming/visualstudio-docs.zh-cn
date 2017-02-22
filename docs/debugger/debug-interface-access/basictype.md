---
title: "BasicType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BasicType 枚举"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定符号的基本类型。  
  
## 语法  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Elements  
 btNoType  
 基本未指定类型。  
  
 btVoid  
 基本类型是 `void`。  
  
 btChar  
 基本类型是 `char` \(C\/C\+\+ 类型\)。  
  
 btWChar  
 基本类型是宽字符 \(unicode\) \(`WCHAR`\)。  
  
 btInt  
 基本类型是 `signed int` \(C\/C\+\+ 类型\)。  
  
 btUInt  
 基本类型是 `unsigned int` \(C\/C\+\+ 类型\)。  
  
 btFloat  
 基本类型是一个浮点数 \(`FLOAT`\)。  
  
 btBCD  
 基本类型是一个二 \- 为十六进制 \(`BCD`\)。  
  
 btBool  
 基本类型是布尔值 \(`BOOL`\)。  
  
 btLong  
 基本类型是 `long int` \(C\/C\+\+ 类型\)。  
  
 btULong  
 基本类型是 `unsigned long int` \(C\/C\+\+ 类型\)。  
  
 btCurrency  
 基本类型是货币。  
  
 btDate  
 基本类型是日期\/时间 \(`DATE`\)。  
  
 btVariant  
 基本类型是可变类型结构 \(`VARIANT`\)。  
  
 btComplex  
 基本类型是一个复数。  
  
 btBit  
 基本类型是位。  
  
 btBSTR  
 基本类型是基或二进制字符串 \(`BSTR`\)。  
  
 btHresult  
 基本类型是 `HRESULT`。  
  
## 备注  
 此枚举的值。 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) 方法返回。  
  
## 要求  
 标题:cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)