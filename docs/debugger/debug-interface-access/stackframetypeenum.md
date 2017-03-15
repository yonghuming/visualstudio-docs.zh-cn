---
title: "StackFrameTypeEnum | Microsoft Docs"
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
  - "StackFrameTypeEnum 枚举"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定堆栈帧类型。  
  
## 语法  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elements  
 `FrameTypeFPO`  
 省略帧指针;可用 FPO 信息。  
  
 `FrameTypeTrap`  
 核心陷阱帧。  
  
 `FrameTypeTSS`  
 核心陷阱帧。  
  
 `FrameTypeStandard`  
 标准 EBP 堆栈帧。  
  
 `FrameTypeFrameData`  
 省略帧指针;可用帧的数据信息。  
  
 `FrameTypeUnknown`  
 没有任何调试信息的帧。  
  
## 备注  
 此枚举的值通过对 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) 方法的调用返回。  
  
## 要求  
 标题:cvconst.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)