---
title: "CallTarget 任务 | Microsoft Docs"
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
  - "CallTarget 任务 [MSBuild]"
  - "MSBuild, CallTarget 任务"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CallTarget 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在项目文件中调用指定的目标。  
  
## 任务参数  
 下表描述了 `CallTarget` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`RunEachTargetSeparately`|可选 `Boolean` 输出参数。<br /><br /> 如果为 `true`，则 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎对每个目标调用一次。  如果为 `false`，则将调用一次 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎以生成所有目标。  默认值为 `false`。|  
|`TargetOutputs`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 包含所有已生成目标的输出。|  
|`Targets`|可选 `String[]` 参数。<br /><br /> 指定要生成的目标。|  
|`UseResultsCache`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则返回缓存的结果（如果存在）。<br /><br /> **注意** 当 MSBuild 任务运行时，其输出以生成项列表的形式缓存在范围（ProjectFileName、GlobalProperties）\[TargetNames\] 中。|  
  
## 备注  
 如果 `Targets` 中指定的某个目标失败且 `RunEachTargetSeparately` 为 `true`，则任务会继续生成剩下的目标。  
  
 如果要生成默认目标，请使用 [MSBuild 任务](../msbuild/msbuild-task.md)并将 `Projects` 参数设为等于 `$(MSBuildProjectFile)`。  
  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例从 `CallOtherTargets` 中调用 `TargetA`。  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [目标](../msbuild/msbuild-targets.md)