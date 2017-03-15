---
title: "FindInList 任务 | Microsoft Docs"
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
  - "FindInList 任务 [MSBuild]"
  - "MSBuild, FindInList 任务"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# FindInList 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在指定的列表中查找具有匹配的项规范的项。  
  
## 参数  
 下表描述了 [FindInList Task](../msbuild/findinlist-task.md)的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`CaseSensitive`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则搜索区分大小写；否则将不区分大小写。  默认值为 `true`。|  
|`FindLastMatch`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则返回最后一个匹配项；否则返回第一个匹配项。  默认值为 `false`。|  
|`ItemFound`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 只读输出参数。<br /><br /> 在列表中发现的第一个匹配项（如果有）。|  
|`ItemSpecToFind`|必选 `String` 参数。<br /><br /> 要搜索的项规范。|  
|`List`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 要在其中搜索项规范的列表。|  
|`MatchFileNameOnly`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则只根据项规范的文件名部分进行匹配；否则将根据整个项规范进行匹配。  默认值为 `true`。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)