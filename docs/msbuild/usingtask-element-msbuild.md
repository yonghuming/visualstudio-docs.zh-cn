---
title: "UsingTask 元素 (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<UsingTask> 元素 [MSBuild]"
  - "UsingTask 元素 [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UsingTask 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将 [Task](../msbuild/task-element-msbuild.md) 元素中引用的任务映射到包含该任务实现的程序集。  
  
## 语法  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`AssemblyName`|`AssemblyName` 属性或 `AssemblyFile` 属性是必需的。<br /><br /> 要加载的程序集的名称。  尽管强命名不是必需的，但是 `AssemblyName` 属性可以接受强名称程序集。  使用此属性等效于使用 .NET 中的 <xref:System.Reflection.Assembly.Load%2A> 方法加载程序集。<br /><br /> 如果使用了 `AssemblyFile` 属性，则不能使用此属性。|  
|`AssemblyFile`|`AssemblyName` 或 `AssemblyFile` 属性是必需的。<br /><br /> 程序集的文件路径。  此属性接受完整路径或相对路径。  相对路径是相对于声明 `UsingTask` 元素的项目文件或目标文件的目录位置而言的。  使用此属性等效于使用 .NET 中的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法加载程序集。<br /><br /> 如果使用了 `AssemblyName` 属性，则不能使用此属性。|  
|`TaskFactory`|可选特性。<br /><br /> 在负责生成指定 `Task` 名称的实例的程序集中指定类。  用户还可以将 `TaskBody` 指定为任务工厂接收并用于生成任务的子元素。  `TaskBody` 的内容特定于任务工厂。|  
|`TaskName`|必需的特性。<br /><br /> 要从程序集中引用的任务的名称。  如果可能存在多义性，则此属性应始终指定完整命名空间。  如果存在多义性，则 MSBuild 将选择任意匹配项，该匹配项可能产生意外结果。|  
|`Condition`|可选特性。<br /><br /> 要计算的条件。  有关详细信息，请参阅 [条件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|参数集，在指定 `TaskFactory` 生成的任务中显示。|  
|[任务](../msbuild/task-element-msbuild.md)|传递给 `TaskFactory` 的数据，用于生成任务的实例。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[Project](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件必需的根元素。|  
  
## 备注  
 如果 `UsingTask` 元素在项目文件中显式显示或通过导入的项目文件显示，则可以在该元素的任意位置引用环境变量、命令行属性和项目级属性。  有关详细信息，请参阅 [任务](../msbuild/msbuild-tasks.md)。  
  
> [!NOTE]
>  如果 `UsingTask` 元素来自使用 MSBuild 引擎进行全局注册的某个 .tasks 文件，则项目级属性没有意义。  项目级属性对于 MSBuild 而言不是全局性的。  
  
 在 MSBuild 4.0 中，可以从 .overridetask 文件加载使用任务。  
  
## 示例  
 下面的示例演示如何将 `UsingTask` 元素和 `AssemblyName` 属性结合使用。  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## 示例  
 下面的示例演示如何将 `UsingTask` 元素和 `AssemblyFile` 属性结合使用。  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)