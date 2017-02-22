---
title: "ResolveNonMSBuildProjectOutput 任务 | Microsoft Docs"
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
helpviewer_keywords: 
  - "MSBuild, ResolveNonMSBuildProjectOutput 任务"
  - "ResolveNonMSBuildProjectOutput 任务 [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveNonMSBuildProjectOutput 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

确定非 MSBuild 项目引用的输出文件。  
  
## 参数  
 下表描述了 `ResolveNonMSBuildProjectOutput` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`PreresolvedProjectOutputs`|可选 `String` 参数。<br /><br /> 指定包含解析的项目输出的 XML 字符串。|  
|`ProjectReferences`|必选的 <xref:Microsoft.Build.Framework.ITaskItem>`[]`  参数。<br /><br /> 指定项目引用。|  
|`ResolvedOutputPaths`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含所解析引用路径的列表（并保留原始项目引用特性）。|  
|`UnresolvedProjectReferences`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含未能使用预解析输出列表进行解析的项目引用项的列表。<br /><br /> 因为 Visual Studio 只预解析非 MSBuild 项目，所以，这就意味着此列表中的项目引用采用的是 MSBuild 格式。|  
  
## 备注  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)