---
title: "AssignTargetPath 任务 | Microsoft Docs"
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# AssignTargetPath 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此任务接受列表文件，并添加 `<TargetPath>` 特性（如果尚未指定）。  
  
## 任务参数  
 下表描述了 `AssignTargetPath` 任务的参数。  
  
|Parameter|描述|  
|---------------|--------|  
|`RootFolder`|可选 `string` 输入参数。<br /><br /> 包含指向包含目标链接的文件夹的路径。|  
|`Files`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 输入参数。<br /><br /> 包含传入文件列表。|  
|`AssignedFiles`|可选<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` 输出参数<br /><br /> 包含生成的文件列表。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例执行 `AssignTargetPath` 项目配置任务。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)