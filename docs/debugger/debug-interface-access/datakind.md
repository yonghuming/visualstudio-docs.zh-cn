---
title: "DataKind | Microsoft Docs"
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
  - "DataKind 枚举"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指示数据值的特定范围。  
  
## 语法  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elements  
 DataIsUnknown  
 数据符号无法确定的。  
  
 DataIsLocal  
 数据项是局部变量。  
  
 DataIsStaticLocal  
 数据项是静态局部变量。  
  
 DataIsParam  
 数据项是形参。  
  
 DataIsObjectPtr  
 数据项是对象指针 \(`this`\)。  
  
 DataIsFileStatic  
 数据项是文件范围变量。  
  
 DataIsGlobal  
 数据项是全局变量。  
  
 DataIsMember  
 数据项是对象成员变量。  
  
 DataIsStaticMember  
 数据项是类的静态变量。  
  
 DataIsConstant  
 数据项是一个常数值。  
  
## 备注  
 此枚举的值。 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) 方法返回。  
  
## 要求  
 标题:cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)