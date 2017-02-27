---
title: "TaskBody 元素 (MSBuild) | Microsoft Docs"
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
  - "<TaskBody> 元素 [MSBuild]"
  - "TaskBody 元素 [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# TaskBody 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含传递给 `UsingTask` `TaskFactory` 的数据。有关更多信息，请参见 [UsingTask 元素 \(MSBuild\)](../msbuild/usingtask-element-msbuild.md)。  
  
## 语法  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|`Evaluate`|可选的布尔特性。<br /><br /> 如果为 `true`，则 MSBuild 先计算任何内部的元素，并扩展项和属性，然后在任务实例化时才将信息传递到 `TaskFactory`。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|数据|`TaskBody` 标记之间的文本原义发送到 `TaskFactory`。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|提供了一种在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中注册任务的方法。  一个项目中可能有零个或零个以上的 `UsingTask` 元素。|  
  
## 示例  
 下面的示例演示如何将 `TaskBody` 元素和 `Evaluate` 特性结合使用。  
  
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