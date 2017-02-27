---
title: "MakeDir 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MakeDir"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MakeDir 任务 [MSBuild]"
  - "MSBuild, MakeDir 任务"
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# MakeDir 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建目录，并在必要时创建任何父目录。  
  
## 参数  
 下表描述了 `MakeDir` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`Directories`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 要创建的目录集。|  
|`DirectoriesCreated`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输出参数。<br /><br /> 此任务创建的目录。  如果未能创建某些目录，则此参数可能不包含传递到 `Directories` 参数中的所有项。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的代码示例使用 `MakeDir` 任务创建 `OutputDirectory` 属性指定的目录。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)