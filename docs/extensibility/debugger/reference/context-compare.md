---
title: "CONTEXT_COMPARE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_COMPARE
helpviewer_keywords: CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48043375ebdf904a7fafbae5e4193b42d8ba8269
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
指定用于比较两个内存上下文的条件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
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
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
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
  
## <a name="members"></a>成员  
 CONTEXT_EQUAL  
 查找列表，它等于目标内存上下文中的第一个内存上下文。  
  
 CONTEXT_LESS_THAN  
 在小于目标内存上下文的列表中找到的第一个内存上下文。  
  
 CONTEXT_GREATER_THAN  
 在大于目标内存上下文的列表中找到的第一个内存上下文。  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 小于或等于目标内存上下文的列表中找到的第一个内存上下文。  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 在大于或等于目标内存上下文的列表中找到的第一个内存上下文。  
  
 CONTEXT_SAME_SCOPE  
 在与目标内存上下文相同作用域中的列表中找到的第一个内存上下文。  
  
 CONTEXT_SAME_FUNCTION  
 在与目标内存作用域相同的功能的列表中找到的第一个内存上下文。  
  
 CONTEXT_SAME_MODULE  
 在中的目标内存上下文相同的模块的列表中找到的第一个内存上下文。  
  
 CONTEXT_SAME_PROCESS  
 在与目标内存上下文相同的进程的列表中找到的第一个内存上下文。  
  
## <a name="remarks"></a>备注  
 作为自变量传递[比较](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)方法。  
  
 这些值用于在满足指定的比较条件列表中找到的第一个内存上下文。 内存上下文提供一组内存上下文将自身针对通过进行比较`IDebugMemoryContext2::Compare`方法。 为其比较运算符的列表中的第一个内存上下文`true`随后会返回。  
  
## <a name="requirements"></a>要求  
 标头： msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 程序集： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)