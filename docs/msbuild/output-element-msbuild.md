---
title: "Output 元素 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> 元素 [MSBuild]"
  - "Output 元素 [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Output 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在项和属性中存储任务输出值。  
  
## 语法  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|`TaskParameter`|必需的特性。<br /><br /> 任务输出参数的名称。|  
|`PropertyName`|`PropertyName` 或 `ItemName` 特性是必需的。<br /><br /> 接收任务输出参数值的属性。  此后，项目可以使用 `$(`*PropertyName*`)` 语法引用该属性。  此属性名称可以是新的属性名称，也可以是已经在项目中定义的名称。<br /><br /> 如果 `ItemName` 还在使用，则不能使用此特性。|  
|`ItemName`|`PropertyName` 或 `ItemName` 特性是必需的。<br /><br /> 接收任务的输出参数值的项。  此后，项目可以使用 `@(`*ItemName*`)` 语法引用该项。  该项的名称可以是新的项名称，也可以是已经在项目中定义的名称。<br /><br /> 如果 `PropertyName` 还在使用，则不能使用此特性。|  
|`Condition`|可选特性。<br /><br /> 要计算的条件。  有关更多信息，请参见 [条件](../msbuild/msbuild-conditions.md)。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[任务](../msbuild/task-element-msbuild.md)|创建并执行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务的一个实例。|  
  
## 示例  
 下面的代码示例演示正在 `Target` 元素内部执行的 `Csc` 任务。  传入到任务参数的项和属性不在本示例中声明。  输出参数 `OutputAssembly` 的值存储在 `FinalAssemblyName` 项中，而输出参数 `BuildSucceeded` 的值存储在 `BuildWorked` 属性中。  有关更多信息，请参见[任务](../msbuild/msbuild-tasks.md)。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## 请参阅  
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)   
 [任务](../msbuild/msbuild-tasks.md)