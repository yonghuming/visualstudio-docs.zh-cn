---
title: "OnError 元素 (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<OnError> 元素 [MSBuild]"
  - "OnError 元素 [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# OnError 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果失败任务的 `ContinueOnError` 特性为 `false`，此元素将引起一个或多个目标执行。  
  
## 语法  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`Condition`|可选特性。<br /><br /> 要计算的条件。  有关更多信息，请参见[条件](../msbuild/msbuild-conditions.md)。|  
|`ExecuteTargets`|必需的特性。<br /><br /> 任务失败时要执行的目标。  用分号分隔多个目标。  多个目标按指定顺序执行。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[Target](../msbuild/target-element-msbuild.md)|包含 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务的元素。|  
  
## 备注  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 执行 `OnError` 元素，如果有一 `Target` 元素的任务而失败。`ContinueOnError` 属性设置为 `ErrorAndStop` \(或 `false`\)。  任务失败后，将执行 `ExecuteTargets` 特性中指定的目标。  如果目标中存在一个以上的 `OnError` 元素，那么当任务失败时，将按顺序执行 `OnError` 元素。  
  
 有关 `ContinueOnError` 属性的信息，请参见 [Task 元素 \(MSBuild\)](../msbuild/task-element-msbuild.md)。  有关对象的信息，请参见 [目标](../msbuild/msbuild-targets.md)。  
  
## 示例  
 下面的代码执行 `TaskOne` 和 `TaskTwo` 任务。  如果 `TaskOne` 失败，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 将计算 `OnError` 元素并执行 `OtherTarget` 目标。  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [目标](../msbuild/msbuild-targets.md)