---
title: "FindAppConfigFile 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "FindAppConfigFile 任务 [MSBuild]"
  - "MSBuild, FindAppConfigFile 任务"
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FindAppConfigFile 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在提供的列表中查找 app.config 文件（如果有任何此类文件）。  
  
## 参数  
 下表描述了 `FindAppConfigFile` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`AppConfigFile`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 指定在列表中发现的第一个匹配项（如果有）。|  
|`PrimaryList`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要对其进行搜索的主列表。|  
|`SecondaryList`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要对其进行搜索的第二个列表。|  
|`TargetPath`|必选 `String` 参数。<br /><br /> 指定要作为元数据添加的值。|  
  
## 备注  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)