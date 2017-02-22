---
title: "Error 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error 任务 [MSBuild]"
  - "MSBuild, Error 任务"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Error 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根据计算的条件语句停止生成操作并记录错误。  
  
## 参数  
 下表描述了 `Error` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`Code`|可选 `String` 参数。<br /><br /> 要与错误关联的错误代码。|  
|`File`|可选 `String` 参数。<br /><br /> 包含错误的文件的名称。  如果未提供任何文件名，则将使用包含“错误”任务的文件。|  
|`HelpKeyword`|可选 `String` 参数。<br /><br /> 与错误关联的“帮助”关键字。|  
|`Text`|可选 `String` 参数。<br /><br /> 当 `Condition` 参数的计算结果为 `true` 时，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 记录的错误文本。|  
  
## 备注  
 `Error` 任务使 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目可以向记录器发出错误文本并停止执行生成。  
  
 如果 `Condition` 参数的计算结果为 `true`，将停止生成，并记录错误。  如果 `Condition` 参数不存在，将记录错误并停止执行生成。  有关日志记录的更多信息，请参见 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的代码示例验证是否所有必需的属性都已设置。  如果未设置这些属性，则项目将引发错误事件，并记录 `Error` 任务的 `Text` 参数的值。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)