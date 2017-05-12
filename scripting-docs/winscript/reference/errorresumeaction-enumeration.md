---
title: "ERRORRESUMEACTION 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ERRORRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ERRORRESUMEACTION 枚举"
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ERRORRESUMEACTION 枚举
描述如何从运行时仍出现错误。  
  
## 语法  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## 成员  
  
|成员|说明|  
|--------|--------|  
|ERRORRESUMEACTION\_ReexecuteErrorStatement|重新实现导致错误的语句。|  
|ERRORRESUMEACTION\_AbortCallAndReturnErrorToCaller|允许语言引擎处理错误。|  
|ERRORRESUMEACTION\_SkipErrorStatement|以遵循导致错误的语句的代码的执行。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)