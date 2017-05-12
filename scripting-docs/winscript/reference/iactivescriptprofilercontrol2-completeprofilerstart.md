---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
通知探查器正在从启动分析在所有适用的脚本引擎。  使用此方法，可以获取完整的调用堆栈，如果 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 运行，则启动分析时。  
  
## 语法  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### 参数  
 该方法不带任何参数。  
  
## 返回值  
 返回HRESULT。  可能值如下：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|分析无法启动。|  
|`S_FALSE`|当脚本不会运行，分析启动。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|分析未启用。  回调尚未设置。|  
|`E_OUTOFMEMORY`|由于内存不足的情况，调用堆栈无法获取。|  
  
## 备注  
 调用 `IActiveScriptProfilerControl2::CompleteProfilerStart` 确保已在调用堆栈发送函数的操作。  此方法必须在分析在当前选项卡的所有脚本引擎的启动后调用。  方法可用于任何脚本引擎调用。  
  
## 请参阅  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 接口](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)