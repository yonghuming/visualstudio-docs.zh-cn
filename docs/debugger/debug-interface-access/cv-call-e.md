---
title: "CV_call_e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_call_e 枚举"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

为功能指定调用约定。  
  
> [!NOTE]
>  仅最常见的枚举值此处。  完整枚举可在 cvconst.h 头文件。  
  
## 语法  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elements  
 CV\_CALL\_NEAR\_C  
 指定使用新的从右向左的驱动器的函数调用约定。  调用函数清除堆栈。  
  
 CV\_CALL\_NEAR\_FAST  
 指定用于注册的函数调用约定最近的从左到右驱动器。  调用函数使用参数字节的总和清除堆栈。  
  
 CV\_CALL\_NEAR\_STD  
 指定使用一个最近的标准的函数调用约定调用 \(从右到左的驱动器\)。  
  
 CV\_CALL\_NEAR\_SYS  
 指定使用新的函数调用约定系统调用。  
  
 CV\_CALL\_THISCALL  
 指定使用 `this` 的函数调用约定调用 \(在传入寄存器的`this` 指针\)。  
  
 CV\_CALL\_CLRCALL  
 指定公共语言运行时使用的函数调用约定 \( \(CLR\)也称为调用约定\) 的托管代码之前。  
  
## 备注  
 此枚举的值通过对 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) 方法的调用返回。  
  
## 要求  
 标题:cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)