---
title: "GenerateTrustInfo 任务 | Microsoft Docs"
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
  - "GenerateTrustInfo 任务 [MSBuild]"
  - "MSBuild, GenerateTrustInfo 任务"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GenerateTrustInfo 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根据基础清单以及 `TargetZone` 和 `ExcludedPermissions` 参数生成应用程序信任。  
  
## 参数  
 下表描述了 `GenerateTrustInfo` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`ApplicationDependencies`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定依赖程序集。|  
|`BaseManifest`|可选 <xref:Microsoft.Build.Framework.ITaskItem> 参数。<br /><br /> 指定生成应用程序信任所依据的基础清单。|  
|`ExcludedPermissions`|可选 `String` 参数。<br /><br /> 指定一个或多个要从区域默认权限集中排除的权限标识值（这些值由分号分隔）。|  
|`TargetZone`|可选 `String` 参数。<br /><br /> 指定区域默认权限集，该权限集是从计算机策略中获取的。|  
|`TrustInfoFile`|必选 <xref:Microsoft.Build.Framework.ITaskItem> 输出参数。<br /><br /> 指定包含应用程序安全信任信息的文件。|  
  
## 备注  
 除了有表中列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)