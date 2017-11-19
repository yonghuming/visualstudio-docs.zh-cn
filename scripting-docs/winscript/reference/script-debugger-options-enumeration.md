---
title: "SCRIPT_DEBUGGER_OPTIONS 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54b910562670104f0fb5679f2b09780afcd17751
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="scriptdebuggeroptions-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS 枚举
指示选项和/或将应用于附加调试器的功能的一组。 在中使用[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)和[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  实现这些常量由 PDM 10.0 版和更高。 在 activdbg100.h 中发现。  
  
## <a name="syntax"></a>语法  
  
```  
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>成员  
  
|成员|值|描述|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|不设置任何选项。|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|指示脚本运行时应引发会发生 BREAKREASON_ERROR 事件时引发异常。 可能由调试器，设置此选项，或将其设置由用户代码通过`Debug.enableFirstChanceExceptions(<true&#124;false>)`。|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|指示连接的调试器支持 web 工作进程。|  
  
## <a name="see-also"></a>另请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)