---
title: "Move 任务 | Microsoft Docs"
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
  - "Move 任务 [MSBuild]"
  - "MSBuild, Move 任务"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Move 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将文件移至新位置。  
  
## 参数  
 下表描述了 `Move` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`DestinationFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 指定源文件要移动到的文件列表。  此列表应与 `SourceFiles` 参数中指定的列表应一一对应。  也就是说，`SourceFiles` 中指定的第一个文件将移到 `DestinationFiles` 中指定的第一个位置，依此类推。|  
|`DestinationFolder`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定文件要移动到的目录。|  
|`MovedFiles`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含成功移动的项。|  
|`OverwriteReadOnlyFiles`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，即使文件被标记为只读文件仍将其覆盖。|  
|`SourceFiles`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要移动的文件。|  
  
## 备注  
 必须指定 `DestinationFolder` 参数或 `DestinationFiles` 参数，但不能同时指定两者。  如果同时指定了这两个参数，则任务将失败，并记录相应的错误。  
  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)