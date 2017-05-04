---
title: "BREAKREASON 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON 枚举"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BREAKREASON 枚举
指示导致该中断。  
  
## 语法  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## 成员  
  
|成员|说明|  
|--------|--------|  
|BREAKREASON\_STEP|语言引擎在单步模式。|  
|BREAKREASON\_BREAKPOINT|语言引擎遇到显式断点。|  
|BREAKREASON\_DEBUGGER\_BLOCK|语言引擎在另一个线程遇到调试器块。|  
|BREAKREASON\_HOST\_INITIATED|宿主请求中断。|  
|BREAKREASON\_LANGUAGE\_INITIATED|语言引擎请求中断。|  
|BREAKREASON\_DEBUGGER\_HALT|调试器IDE请求中断。|  
|BREAKREASON\_ERROR|执行错误导致该中断。|  
|BREAKREASON\_JIT|导致调试启动的JIT。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)