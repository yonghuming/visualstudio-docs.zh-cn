---
title: "CreateProperty 任务 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty 任务 [MSBuild]"
  - "MSBuild, CreateProperty 任务"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CreateProperty 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用传入的值来填充属性。  这允许将值从一个属性或字符串复制到另一个属性或字符串。  
  
## 特性  
 下表描述了 `CreateProperty` 任务的参数。  
  
|Parameter|说明|  
|---------------|--------|  
|`Value`|可选 `String` 输出参数。<br /><br /> 指定要复制到新属性的值。|  
|`ValueSetByTask`|可选 `String` 输出参数。<br /><br /> 包含与 `Value` 参数相同的值。  只有在以下情况下才使用此参数：您想避免因输出处于最新状态而跳过结束目标时由 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 设置输出属性。|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## 示例  
 下面的示例使用 `CreateProperty` 任务来创建 `NewFile` 属性，该属性采用了 `SourceFilename` 和 `SourceFileExtension` 属性的值的组合。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 运行项目后，`NewFile` 属性的值为 `Module1.vb`。  
  
## 请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [任务](../msbuild/msbuild-tasks.md)