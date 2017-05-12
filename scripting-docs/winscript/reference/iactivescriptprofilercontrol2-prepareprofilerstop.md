---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
通知探查器可以停止分析在所有适用的脚本引擎。  使用此方法，可以获取完整的调用堆栈，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行，当停止分析。  
  
## 语法  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### 参数  
 该方法不带任何参数。  
  
## 返回值  
 返回HRESULT。  可能值如下：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|分析无法启动。|  
|`S_FALSE`|当脚本不会运行，分析已停止运行。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|分析未启用。|  
  
## 备注  
 调用 `IActiveScriptProfilerControl2::PrepareProfilerStop` 确保在调用堆栈发送函数的操作。  此方法必须先调用，然后停止分析在当前选项卡的所有脚本引擎之前。  方法可用于任何脚本引擎调用。  
  
## 请参阅  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 接口](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)