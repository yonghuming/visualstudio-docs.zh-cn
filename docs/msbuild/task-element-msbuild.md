---
title: "Task 元素 (MSBuild) | Microsoft Docs"
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
  - "<Task> 元素 [MSBuild]"
  - "Task 元素 [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Task 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建并执行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务的一个实例。  元素名称由正在创建的任务的名称决定。  
  
## 语法  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`Condition`|可选特性。  要计算的条件。  有关更多信息，请参见[条件](../msbuild/msbuild-conditions.md)。|  
|`ContinueOnError`|可选特性。  可以包含下列值之一：<br /><br /> -   **WarnAndContinue** 或 **真**。  当任务失败时，在 [目标](../msbuild/target-element-msbuild.md) 元素和生成的后续任务继续执行，因此，从任务的所有错误视为警告。<br />-   **ErrorAndContinue**。  当任务失败时，在 `Target` 元素和生成的后续任务继续执行，因此，从任务的所有错误视为错误。<br />-   **ErrorAndStop** 或 **假** \(默认值\)。  当任务失败时，在 `Target` 元素和生成的余下的任务，不会执行，整个 `Target` 元素和编译考虑失败。<br /><br /> .NET Framework 的版本在 4.5 版之前的仅支持 `true` 和 `false` 值。<br /><br /> 有关更多信息，请参见[如何：忽略任务中的错误](../Topic/How%20to:%20Ignore%20Errors%20in%20Tasks.md)。|  
|`Parameter`|如果任务类包含一个或多个带有 `[Required]` 特性标记的属性，则此特性为必选。<br /><br /> 用户定义的任务参数，包含作为它的值的参数值。  `Task` 元素中可以有任意数目的参数，其每个特性均映射到任务类中的一个 .NET 属性。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[Output](../msbuild/output-element-msbuild.md)|将来自任务的输出存储在项目文件中。  一个任务中可能有零个或零个以上的 `Output` 元素。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[Target](../msbuild/target-element-msbuild.md)|包含 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务的元素。|  
  
## 备注  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件中的 `Task` 元素创建一个任务实例，并设置该任务的属性，然后执行该任务。  `Output` 元素将输出参数存储在要用在项目文件的其他位置的属性或项中。  
  
 如果任务的父 `Target` 元素中存在任何 [OnError](../msbuild/onerror-element-msbuild.md) 元素，则当任务失败并且 `ContinueOnError` 的值为 `false` 时，仍会计算这些元素。  有关任务的更多信息，请参见 [任务](../msbuild/msbuild-tasks.md)。  
  
## 示例  
 下面的代码示例创建 [Csc task](../msbuild/csc-task.md) 类的一个实例，设置六个属性，然后执行该任务。  执行后，对象的 `OutputAssembly` 属性的值将放入名为 `FinalAssemblyName` 的项列表中。  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)