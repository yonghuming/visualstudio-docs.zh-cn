---
title: "APPBREAKFLAGS 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS 常量"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# APPBREAKFLAGS 枚举
指示当前调试应用程序和线程的状态。  
  
## 语法  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|语言引擎立即在与BREAKREASON\_DEBUGGER\_BLOCK的所有线程都应中断。|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|语言引擎应立即中断与BREAKREASON\_DEBUGGER\_HALT。|  
|APPBREAKFLAG\_STEP|0x00010000|语言引擎立即在与BREAKREASON\_STEP的单步执行线程应该中断。|  
|APPBREAKFLAG\_NESTED|0x00020000|应用程序在断点的嵌套执行。|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|调试器单步执行源级别。|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|调试器单步执行字节代码级别。|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|调试器逐句在计算机级别。|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|分解的步骤类型掩码。|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|断点正在进行。|  
  
## 备注  
 某些标志指定语言引擎应中断在下的机会，而其他标志指定调试器中逐句模式。  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON 枚举](../../winscript/reference/breakreason-enumeration.md)