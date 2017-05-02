---
title: "活动脚本分析概述 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "活动脚本分析"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 活动脚本分析概述
[活动脚本探查器接口](../winscript/reference/active-script-profiler-interfaces.md) 启用分析一个脚本引擎。  事件脚本分析由以下部分组成：  
  
-   语言引擎  
  
-   主机  
  
-   探查器  
  
## 语言引擎  
 语言引擎执行该脚本。  它提供允许分析脚本代码的方法，该方法执行。  当分析处于启用状态，语言引擎采用选件类标识符 \(CLSID\) 探查器 COM 对象作为参数。  在各种事件发生时，它会创建探查器 COM 对象的实例并调用到探查器。  
  
 语言引擎实现 [IActiveScriptProfilerControl 接口](../winscript/reference/iactivescriptprofilercontrol-interface.md)。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] 语言运行时检查中创建的 JS\_PROFILER 环境变量确定是否应启用分析。  如果此变量设置为探查器的 CLSID，语言运行时创建探查器 COM 对象的实例，使用变量的值决定创建哪个探查器。  
  
## 主机  
 宿主创建语言引擎并提供语言引擎与要执行的脚本。  一个智能宿主还提供可供调试器或探查器用于提供更好的信息的文档上下文进行调试时，或分析时。  
  
## 探查器  
 在各种事件时，探查器收到来自语言引擎调用。  必须注册探查器为 COM 对象，并且必须实现 [IActiveScriptProfilerCallback 接口](../winscript/reference/iactivescriptprofilercallback-interface.md) 接口。  
  
## 请参阅  
 [活动脚本探查器接口](../winscript/reference/active-script-profiler-interfaces.md)