---
title: "CV_CFL_LANG | Microsoft Docs"
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
  - "CV_CFL_LANG 枚举"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定应用或链接摸块的源代码语言。  
  
## 语法  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## Elements  
 CV\_CFL\_C  
 应用程序语言是C。  
  
 CV\_CFL\_CXX  
 应用程序语言为C\+\+。  
  
 CV\_CFL\_FORTRAN  
 应用程序是语言编写的。  
  
 CV\_CFL\_MASM  
 应用程序语言是Microsoft Macro Assembler。  
  
 CV\_CFL\_PASCAL  
 应用程序是Pascal语言。  
  
 CV\_CFL\_BASIC  
 应用程序语言是原子的。  
  
 CV\_CFL\_COBOL  
 应用程序是COBOL语言。  
  
 CV\_CFL\_LINK  
 应用程序是一个链接器生成的模块。  
  
 CV\_CFL\_CVTRES  
 应用程序是资源模块将带CVTRES工具。  
  
 CV\_CFL\_CVTPGD  
 应用程序是POGO优化模块生成与CVTPGD工具。  
  
 CV\_CFL\_CSHARP  
 应用程序语言是C\#。  
  
 CV\_CFL\_VB  
 应用程序语言是Visual Basic。  
  
 CV\_CFL\_ILASM  
 应用程序语言为中间语言程序集\(即公共语言运行时\(CLR\)程序集\)。  
  
 CV\_CFL\_JAVA  
 应用程序是Java语言。  
  
 CV\_CFL\_JSCRIPT  
 应用程序是Jscript语言。  
  
 CV\_CFL\_MSIL  
 应用程序语言是一种未知的Microsoft中间语言\(msil\)，可以使用结果 [\/LTCG（链接时代码生成）](/visual-cpp/build/reference/ltcg-link-time-code-generation) 开关。  
  
 CV\_CFL\_HLSL  
 应用程序语言是高级着色器语言。  
  
## 备注  
 此枚举的值调用并返回到 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md) 方法。  
  
## 要求  
 头文件：cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)