---
title: "REFERENCE_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "REFERENCE_COMPARE"
helpviewer_keywords: 
  - "REFERENCE_COMPARE 枚举"
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# REFERENCE_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定比较的类型为引用。  
  
## 语法  
  
```cpp#  
enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
typedef DWORD REFERENCE_COMPARE;  
```  
  
```c#  
public enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
```  
  
## 成员  
 REF\_COMPARE\_EQUAL  
 指定等于比较。  
  
 REF\_COMPARE\_LESS\_THAN  
 指定小于比较。  
  
 REF\_COMPARE\_GREATER\_THAN  
 指定大于比较。  
  
## 备注  
 将作为参数传递 [比较](../../../extensibility/debugger/reference/idebugreference2-compare.md) 方法。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [比较](../../../extensibility/debugger/reference/idebugreference2-compare.md)