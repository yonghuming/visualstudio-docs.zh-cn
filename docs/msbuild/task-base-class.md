---
title: "任务基类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 任务基类
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

很多任务最终从 <xref:Microsoft.Build.Utilities.Task> 类继承。  此类向任务添加几个派生自它们的参数。  此本文档中列出了这些参数。  
  
## 参数  
 下表描述了此基类的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|可选 <xref:Microsoft.Build.Framework.IBuildEngine> 参数。<br /><br /> 指定任务可用的生成引擎接口。  生成引擎自动设置此参数，以允许任务回调此生成引擎。|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|可选 <xref:Microsoft.Build.Framework.IBuildEngine2> 参数。<br /><br /> 指定任务可用的生成引擎接口。  生成引擎自动设置此参数，以允许任务回调此生成引擎。<br /><br /> 这是一个便捷属性，以便从该类进行继承的任务作者不必将该值从 `IBuildEngine` 强制转换为  `IBuildEngine2`。|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|可选 <xref:Microsoft.Build.Framework.IBuildEngine3> 参数。<br /><br /> 指定由主机提供的生成引擎接口。|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|可选 <xref:Microsoft.Build.Framework.ITaskHost> 参数。<br /><br /> 指定主机对象实例（可以为 null）。  如果宿主 IDE 已将某个宿主对象与该特定任务关联，则由生成引擎设置此属性。|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|可选 <xref:Microsoft.Build.Utilities.TaskLoggingHelper> 只读参数。<br /><br /> 记录帮助器对象。|  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [任务](../msbuild/msbuild-tasks.md)