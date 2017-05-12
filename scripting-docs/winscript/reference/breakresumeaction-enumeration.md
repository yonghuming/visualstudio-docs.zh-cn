---
title: "BREAKRESUMEACTION 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION 枚举"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKRESUMEACTION 枚举
描述从断点继续的方法。  
  
## 语法  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Members  
  
|成员|描述|  
|--------|--------|  
|BREAKRESUMEACTION\_ABORT|中止应用程序。|  
|BREAKRESUMEACTION\_CONTINUE|继续运行。|  
|BREAKRESUMEACTION\_STEP\_INTO|单步执行过程。|  
|BREAKRESUMEACTION\_STEP\_OVER|逐过程执行过程。|  
|BREAKRESUMEACTION\_STEP\_OUT|跳出当前过程。|  
|BREAKRESUMEACTION\_IGNORE|继续运行状态。|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|进入下一个文档。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)