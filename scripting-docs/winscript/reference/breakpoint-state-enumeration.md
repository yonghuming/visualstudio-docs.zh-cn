---
title: "BREAKPOINT_STATE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKPOINT_STATE 枚举"
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKPOINT_STATE 枚举
指示断点的状态。  
  
## 语法  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## 成员  
  
|成员|说明|  
|--------|--------|  
|BREAKPOINT\_DELETED|断点不再存在，但是，仍有对它的引用。|  
|BREAKPOINT\_DISABLED|断点存在，但已被禁用。|  
|BREAKPOINT\_ENABLED|断点存在且已启用。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)