---
title: "Target 元素 (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Target 元素 [MSBuild]"
  - "<Target> 元素 (MSBuild)"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Target 元素 (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的一组任务，这组任务应按顺序执行。  
  
## 语法  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`Name`|必需的特性。<br /><br /> 目标的名称。|  
|`Condition`|可选特性。<br /><br /> 要计算的条件。  如果条件的计算结果为 `false`，目标将不会执行该目标的体或者在 `DependsOnTargets` 特性中设置的任何目标的体。  有关条件的更多信息，请参见 [条件](../msbuild/msbuild-conditions.md)。|  
|`Inputs`|可选特性。<br /><br /> 来自输入到此目标的文件。  多文件之间用分号分隔。  文件的时间戳和文件比较的时间戳。`Outputs` 的确定 `Target` 是否是最新的。  有关更多信息，请参见[增量生成](../msbuild/incremental-builds.md)、[如何：增量生成](../msbuild/how-to-build-incrementally.md)和[转换](../msbuild/msbuild-transforms.md)。|  
|`Outputs`|可选特性。<br /><br /> 窗体输出到此目标的文件。  多文件之间用分号分隔。  文件的时间戳和文件比较的时间戳。`Inputs` 的确定 `Target` 是否是最新的。  有关更多信息，请参见[增量生成](../msbuild/incremental-builds.md)、[如何：增量生成](../msbuild/how-to-build-incrementally.md)和[转换](../msbuild/msbuild-transforms.md)。|  
|`Returns`|可选特性。<br /><br /> 将可用于调用此目标的任务（例如，MSBuild 任务）的项目集。  多个目标之间用分号分隔。  如果在文件的目标没有 `Returns` 属性，因此使用输出属性。|  
|`KeepDuplicateOutputs`|可选的布尔特性。<br /><br /> 如果 `true`，多个对目标的 Returns 的同一项目中记录。  默认情况下，此特性为 `false`。|  
|`BeforeTargets`|可选特性。<br /><br /> 分号分隔的目标名称列表。如果指定，指示此目标应当在指定的目标或目标之前运行。  这允许项作者扩展存在设置目标，而无需直接修改它们。  有关更多信息，请参见[目标生成顺序](../msbuild/target-build-order.md)。|  
|`AfterTargets`|可选特性。<br /><br /> 分号分隔的目标名称列表。  如果指定，指示此目标应当在指定的目标或目标。  这允许项作者扩展存在设置目标，而无需直接修改它们。  有关更多信息，请参见[目标生成顺序](../msbuild/target-build-order.md)。|  
|`DependsOnTargets`|可选特性。<br /><br /> 在可以执行此目标或者进行顶级依赖项分析之前必须执行的目标。  多个目标之间用分号分隔。|  
|`Label`|可选特性。<br /><br /> 可以标识或命令系统和用户元素的标识符。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[任务](../msbuild/task-element-msbuild.md)|创建并执行 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务的一个实例。  一个目标中可以有零个或零个以上的任务。|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|包含一组用户定义的 `Property` 元素。  .NET framework 3.5 开始，`Target` 元素可以包含 `PropertyGroup` 元素。|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|包含一组用户定义的 `Item` 元素。  .NET framework 3.5 开始，`Target` 元素可以包含 `ItemGroup` 元素。  有关更多信息，请参见[项](../msbuild/msbuild-items.md)。|  
|[OnError](../msbuild/onerror-element-msbuild.md)|分配给一个或多个目标，则执行 `ContinueOnError` 属性是 ErrorAndStop \(或\) `false`一个失败的任务。  一个目标中可以有零个或零个以上的 `OnError` 元素。  如果 `OnError` 元素存在，则它们必须是 `Target` 元素中的最后元素。<br /><br /> 有关 `ContinueOnError` 属性的信息，请参见" [Task 元素 \(MSBuild\)](../msbuild/task-element-msbuild.md)。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[项目](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件必需的根元素。|  
  
## 备注  
 要执行的第一个目标在运行时指定。  目标可能依赖于其他目标。  例如，要部署的目标依赖于要编译的目标。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎按照依赖项在 `DependsOnTargets` 特性中的显示顺序，从左至右依次执行这些依赖项。  有关更多信息，请参见[目标](../msbuild/msbuild-targets.md)。  
  
 一个目标在生成过程中仅执行一次，即便有多个目标依赖于它也是如此。  
  
 如果由于某个目标的 `Condition` 特性的计算结果为 `false` 而跳过了该目标，但是在生成过程的后期调用该目标，并且它的 `Condition` 特性在当时的计算结果为 `true`，那么仍然可以执行该目标。  
  
 在 MSBuild 4 之前，`Target` 返回的是在 `Outputs` 特性中指定的任何项。  为此，MSBuild 必须在稍后的用例任务中，将这些项记录在请求它们的生成中。  因为没有办法指示哪些目标有调用方需要的输出，所以 MSBuild 积累了调用的所有 `Target` 上的所有 `Outputs` 中的所有项目。  这对于拥有大量输出项的生成，会导致缩放问题。  
  
 如果用户在项目的任何 `Target` 元素上指定 `Returns`，则只有拥有 `Returns` 特性的 `Target` 才记录这些项目。  
  
 `Target` 可以包含 `Outputs` 特性和 `Returns` 特性。  `Outputs` 与  `Inputs` 一起使用，确定目标是否最新。  如果存在，`Returns` 将重写 `Outputs` 的值，以确定将哪些项返回给调用方。  如果 `Returns` 不存在，则 `Outputs` 将可用于调用方，前面所述的情况除外。  
  
 MSBuild 4 之前，任何时间 `Target` 都在其  `Outputs` 中包括了对同一项的多个引用，这些重复的项目都会被记录。  在有大量输出和许多项目相互依赖项的非常大的生成中，这会导致大量的内存浪费，因为重复的项目没有任何用途。  当 `KeepDuplicateOutputs` 属性设置为 `true`时，这些重复登录。  
  
## 示例  
 下面的代码示例演示执行 `Csc` 任务的 `Target` 元素。  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
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
 [目标](../msbuild/msbuild-targets.md)   
 [项目文件架构参考](../msbuild/msbuild-project-file-schema-reference.md)