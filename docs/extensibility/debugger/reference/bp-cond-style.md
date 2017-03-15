---
title: "BP_COND_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "BP_COND_STYLE 枚举"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

为挂起和绑定断点指定断点条件样式。  
  
## 语法  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## 成员  
 BP\_COND\_NONE  
 ，在断点位置时，激发断点。  未指定的断点条件。  
  
 BP\_COND\_WHEN\_TRUE  
 ，仅当在条件表达式与断点计算结果为 `true`时，激发断点。  
  
 BP\_COND\_WHEN\_CHANGED  
 ，仅当在条件表达式的值与断点从以前的计算时，更改时激发断点。  
  
## 备注  
 用于 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 结构的 `styleCondition` 成员。  
  
## 要求  
 标题:msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)