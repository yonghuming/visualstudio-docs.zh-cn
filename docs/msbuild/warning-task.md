---
title: "Warning 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Warning 任务"
  - "Warning 任务 [MSBuild]"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Warning 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根据计算的条件语句在生成期间记录警告。  
  
## 参数  
 下表描述了 `Warning` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`Code`|可选 `String` 参数。<br /><br /> 要与警告相关联的警告代码。|  
|`File`|可选 `String` 参数。<br /><br /> 指定相关文件（如果有）。  如果未提供任何文件，则将使用包含“警告”任务的文件。|  
|`HelpKeyword`|可选 `String` 参数。<br /><br /> 与警告关联的“帮助”关键字。|  
|`Text`|可选 `String` 参数。<br /><br /> 当 `Condition` 参数的计算结果为 `true` 时，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 记录的警告文本。|  
  
## 备注  
 `Warning` 任务使 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目可以在继续下一个生成步骤之前，先检查必需的配置或属性是否存在。  
  
 当 `Warning` 任务的 `Condition` 参数的计算结果为 `true` 时，将记录 `Text` 参数的值，并继续执行生成操作。  如果 `Condition` 参数不存在，则记录警告文本。  有关日志记录的更多信息，请参见 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的代码示例检查在命令行上设置的属性。  如果未设置任何属性，则项目将引发警告事件，并记录 `Warning` 任务的 `Text` 参数的值。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 请参阅  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)