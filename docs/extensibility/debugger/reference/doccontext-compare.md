---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
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
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "DOCCONTEXT_COMPARE 枚举"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用于比较两个指定标准文档上下文。  
  
## 语法  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## 成员  
 DOCCONTEXT\_EQUAL  
 查找第一个文档与其目标是相等的文档上下文的列表的上下文。  
  
 DOCCONTEXT\_LESS\_THAN  
 查找第一个文档与该目标小于的列表的上下文文档上下文。  
  
 DOCCONTEXT\_GREATER\_THAN  
 查找第一个文档与该目标大的列表的上下文文档上下文。  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 查找第一个文档上的列表的上下文同一文档，该文档目标上下文。  
  
## 备注  
 将作为参数传递 [比较](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) 方法。  
  
 这些值用于查找第一指定比较条件文档列表的上下文。  为文档上下文中的文档上下文传递 `IDebugDocumentContext2::Compare` 方法比较自身。  第一个文档比较运算符是 `true` 则返回的列表的上下文。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比较](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)