---
title: "GetReferenceAssemblyPaths 任务 | Microsoft Docs"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GetReferenceAssemblyPaths 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

返回各种框架的引用程序集路径。  
  
## 参数  
 下表描述了 `GetReferenceAssemblyPaths` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`ReferenceAssemblyPaths`|可选 `String[]` 输出参数。<br /><br /> 基于 `TargetFrameworkMoniker` 参数返回路径。  如果 `TargetFrameworkMoniker` 为 null 或为空，则此路径将为 `String.Empty`。|  
|`FullFrameworkReferenceAssemblyPaths`|可选 `String[]` 输出参数。<br /><br /> 基于 `TargetFrameworkMoniker` 参数返回路径，而无需考虑名字对象的配置文件部分。  如果 `TargetFrameworkMoniker` 为 null 或为空，则此路径将为 `String.Empty`。|  
|`TargetFrameworkMoniker`|可选 `String` 参数。<br /><br /> 指定与引用程序集路径关联的目标框架名字对象。|  
|`RootPath`|可选 `String` 参数。<br /><br /> 指定用于生成引用程序集路径的根路径。|  
|`BypassFrameworkInstallChecks`|可选 [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) 参数。<br /><br /> 如果为 `true`，则绕过 `GetReferenceAssemblyPaths` 默认情况下执行的基本检查，以确保根据目标框架安装了某些运行时框架。|  
|`TargetFrameworkMonikerDisplayName`|可选 `String` 输出参数。<br /><br /> 指定目标框架名字对象的显示名称。|  
  
## 备注  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)