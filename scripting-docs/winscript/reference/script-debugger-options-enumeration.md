---
title: "SCRIPT_DEBUGGER_OPTIONS 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SCRIPT_DEBUGGER_OPTIONS 枚举"
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPT_DEBUGGER_OPTIONS 枚举
指示应用于附加调试器的设置选项和功能。  使用在 [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 和 [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  这些常量由PDM v10.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|SDO\_NONE|0x00000000|未设置选项。|  
|SDO\_ENABLE\_FIRST\_CHANCE\_EXCEPTIONS|0x00000001|指示脚本运行时应引发BREAKREASON\_ERROR事件，引发异常。  此选项可以由调试器设置或由用户代码设置。`Debug.enableFirstChanceExceptions(<true&#124;false>)`。|  
|SDO\_ENABLE\_WEB\_WORKER\_SUPPORT|0x00000002|指示附加调试器支持web辅助。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)