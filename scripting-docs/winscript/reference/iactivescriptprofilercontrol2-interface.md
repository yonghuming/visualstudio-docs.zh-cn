---
title: "IActiveScriptProfilerControl2 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2 接口"
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2 接口
提供添加能够开始或停止分析方法脚本运行时间。  
  
## 方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|通知探查器正在从启动分析在所有适用的脚本引擎。  这使您可以获取完整的调用堆栈，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行，则启动分析时。|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|通知探查器可以停止分析在所有适用的脚本引擎。  这使您可以获取完整的调用堆栈，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行，当停止分析。|  
  
## 请参阅  
 [IActiveScriptProfilerControl 接口](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [活动脚本探查器接口](../../winscript/reference/active-script-profiler-interfaces.md)