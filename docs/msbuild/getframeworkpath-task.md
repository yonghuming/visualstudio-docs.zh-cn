---
title: "GetFrameworkPath 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath 任务 [MSBuild]"
  - "MSBuild, GetFrameworkPath 任务"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetFrameworkPath 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

检索 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程序集的路径。  
  
## 任务参数  
 下表描述了 `GetFrameworkPath` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`FrameworkVersion11Path`|可选 `String` 输出参数。<br /><br /> 包含指向框架 1.1 版本程序集的路径（如果存在）。  否则，返回 `null`。|  
|`FrameworkVersion20Path`|可选 `String` 输出参数。<br /><br /> 包含指向框架 2.0 版本程序集的路径（如果存在）。  否则，返回 `null`。|  
|`FrameworkVersion30Path`|可选 `String` 输出参数。<br /><br /> 包含指向框架 3.0 版本程序集的路径（如果存在）。  否则，返回 `null`。|  
|`FrameworkVersion35Path`|可选 `String` 输出参数。<br /><br /> 包含指向框架 3.5 版本程序集的路径（如果存在）。  否则，返回 `null`。|  
|`FrameworkVersion40Path`|可选 `String` 输出参数。<br /><br /> 包含指向框架 4.0 版本程序集的路径（如果存在）。  否则，返回 `null`。|  
|`Path`|可选 `String` 输出参数。<br /><br /> 包含指向最新框架程序集的路径（如果任何程序集可用）。  否则，返回 `null`。|  
  
## 备注  
 如果安装了多个版本的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，则此任务将返回设计在其上运行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的版本。  
  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例使用 `GetFrameworkPath` 任务将 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的路径存储在 `FrameworkPath` 属性中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)