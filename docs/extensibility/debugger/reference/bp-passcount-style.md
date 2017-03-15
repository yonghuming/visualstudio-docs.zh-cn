---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "BP_PASSCOUNT_STYLE 结构"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定条件与将断点激发的断点通过计数。  
  
## 语法  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## 成员  
 BP\_PASSCOUNT\_NONE  
 未指定断点通过计数样式。  
  
 BP\_PASSCOUNT\_EQUAL  
 设置断点通过计数等于样式。  断点个; 当个断点的命中次数等于通过计数。  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 设置断点通过计数样式相同或更大。  断点个; 当断点的命中次数等于或大于通过计数。  
  
 BP\_PASSCOUNT\_MOD  
 指定取模通过计数。  例如，因此，如果通过计数是类型 `BP_PASSCOUNT_MOD` ，并将绑定值为 4，断点激发时，在命中次数是多线程的 4. 时间。  
  
## 备注  
 用于页的 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 结构的成员 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 结构的 `stylePassCount` 成员。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)