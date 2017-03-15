---
title: "Parameter 元素 | Microsoft Docs"
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
  - "<Parameter> 元素 [MSBuild]"
  - "Parameter 元素 [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Parameter 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含有关任务的特定参数的信息，该任务由 `UsingTask``TaskFactory` 生成。元素的名称即为参数的名称。有关更多信息，请参见 [UsingTask 元素 \(MSBuild\)](../msbuild/usingtask-element-msbuild.md)。  
  
## 语法  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|`ParameterType`|可选特性。<br /><br /> 参数的The .NET 类型，例如，"System.String"。|  
|`Output`|可选的布尔特性。<br /><br /> 如果为 `true`，则此参数为任务的输出参数。  默认情况下，此值为 `false`。|  
|`Required`|可选的布尔特性。<br /><br /> 如果为 `true`，则此参数是该任务必需的参数。  默认情况下，此值为 `false`。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|包含可选的参数列表，将在由 `UsingTask``TaskFactory` 生成的任务上的显示出来。|  
  
## 示例  
 下面的示例演示如何使用 `Parameter` 元素。  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)