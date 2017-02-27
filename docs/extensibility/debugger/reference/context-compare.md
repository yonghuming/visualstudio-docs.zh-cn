---
title: "CONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "CONTEXT_COMPARE 枚举"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用于比较两个内存上下文指定条件。  
  
## 语法  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## 成员  
 CONTEXT\_EQUAL  
 查找与目标内存上下文相等列表中的第一个内存上下文。  
  
 CONTEXT\_LESS\_THAN  
 查找比目标内存上下文小于的列表的第一个内存上下文。  
  
 CONTEXT\_GREATER\_THAN  
 查找比目标内存上下文大的列表中的第一个内存上下文。  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 查找小于或等于目标内存上下文的列表的第一个内存上下文。  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 查找大于或等于目标内存上下文的列表的第一个内存上下文。  
  
 CONTEXT\_SAME\_SCOPE  
 查找在范围和目标内存上下文相同的列表的第一个内存上下文。  
  
 CONTEXT\_SAME\_FUNCTION  
 查找在功能和目标内存范围相同的列表的第一个内存上下文。  
  
 CONTEXT\_SAME\_MODULE  
 查找在模块和目标内存上下文相同的列表的第一个内存上下文。  
  
 CONTEXT\_SAME\_PROCESS  
 在中找到列表中的第一个内存上下文同一进程作为目标内存上下文。  
  
## 备注  
 将作为参数传递 [比较](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) 方法。  
  
 这些值用于查找满足指定的比较条件的列表中的第一个内存上下文。  为内存上下文内存上下文列出比较自己的传递 `IDebugMemoryContext2::Compare` 方法。  比较运算符是 `true` 的列表的第一个内存上下文然后返回。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比较](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)