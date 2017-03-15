---
title: "STEPUNIT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPUNIT"
helpviewer_keywords: 
  - "STEPUNIT 枚举"
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPUNIT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

对单步执行指定步骤单元。  
  
## 语法  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```c#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## 成员  
 STEP\_STATEMENT  
 由语句的步骤。  
  
 STEP\_LINE  
 由行的步骤。  
  
 STEP\_INSTRUCTION  
 由命令的步骤。  
  
## 备注  
 将作为参数传递 [单步执行](../../../extensibility/debugger/reference/idebugprocess3-step.md) 方法。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [单步执行](../../../extensibility/debugger/reference/idebugprocess3-step.md)