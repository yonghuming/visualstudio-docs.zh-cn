---
title: "MSBuild 任务 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild 任务 [MSBuild]"
  - "MSBuild, MSBuild 任务"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 任务
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

基于一个 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目生成另一个 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目。  
  
## 参数  
 下表描述了 `MSBuild` 任务的参数。  
  
|Parameter|描述|  
|---------------|--------|  
|`BuildInParallel`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则尽可能并行生成在 `Projects` 参数中指定的项目。  默认值为 `false`。|  
|`Projects`|必选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 参数。<br /><br /> 指定要生成的项目文件。|  
|`Properties`|可选 `String` 参数。<br /><br /> 以分号分隔的属性名称\/值对列表，这些属性名称\/值对将作为全局属性应用于子项目。  当使用 [MSBuild.exe](../msbuild/msbuild-command-line-reference.md) 生成项目时，指定此参数在功能上等效于设置具有 **\/property** 开关的属性。  例如：<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> 通过 `Properties` 参数向项目传递属性时，即使已加载项目文件，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 也会创建该项目的一个新实例。  创建项目的新实例后，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 会将其视为具有不同的全局属性并且可与该项目的其他实例并行生成的不同项目。  例如，“发布”配置可与“调试”配置同时生成。|  
|`RebaseOutputs`|可选 `Boolean` 参数。<br /><br /> 如果设置为 `true`，生成项目中目标输出项的相对路径将调整为相对于调用项目的路径。  默认值为 `false`。|  
|`RemoveProperties`|可选 `String` 参数。<br /><br /> 指定要移除的全局属性集。|  
|`RunEachTargetSeparately`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务将一次调用一个传递给 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的列表中的目标，而不是同时调用这些目标。  将此参数设置为 `true` 可保证即使先前调用的目标失败，仍调用后续目标。  否则，生成错误将停止对所有后续目标的调用。  默认值为 `false`。|  
|`SkipNonexistentProjects`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将跳过磁盘上不存在的项目文件。  否则，这些项目将导致错误。|  
|`StopOnFirstFailure`|可选 `Boolean` 参数。<br /><br /> 如为 `true`，则其中一个项目的生成会失败，不会生成更多的项目。  目前这不被并行（具有多个处理器）生成所支持。|  
|`TargetAndPropertyListSeparators`|可选 `String[]` 参数。<br /><br /> 指定目标和属性如 `Project` 元数据）的列表。  分隔符将在处理之前取消转义。  即.. %3B \(转义“; ’\) 将处理，就象非转义“;”。|  
|`TargetOutputs`|可选 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 只读输出参数。<br /><br /> 从所有项目文件返回已生成目标的输出。  只返回指定目标中的输出，不返回这些目标所依赖的目标中可能存在的任何输出。<br /><br /> `TargetOutputs` 参数还包含以下元数据：<br /><br /> -   `MSBuildSourceProjectFile`：包含设置输出的目标的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件。<br />-   `MSBuildSourceTargetName`：设置输出的目标。 **Note:**  如果要单独标识每个项目文件或目标中的输出，可以为每个项目文件或目标单独运行 `MSBuild` 任务。  如果仅通过运行一次 `MSBuild` 任务来生成所有的项目文件，那么所有目标的输出都将会收集到一个数组中。|  
|`Targets`|可选 `String` 参数。<br /><br /> 指定要在项目文件中生成的一个或多个目标。  使用分号分隔目标名称列表。  如果 `MSBuild` 任务中未指定目标，将会生成项目文件中指定的默认目标。 **Note:**  目标必须存在于所有的项目文件中。  如果这些目标不存在，将会出现生成错误。|  
|`ToolsVersion`|可选 `String` 参数。<br /><br /> 指定要在生成项目传递给此任务时使用的 `ToolsVersion`。<br /><br /> 使 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务生成一个项目，该项目面向与项目中指定的版本不同的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本。  有效值为 `2.0`、`3.0` 和 `3.5`。  默认值为 `3.5`。|  
|`UnloadProjectsOnCompletion`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则在操作完成后将卸载项目。|  
|`UseResultsCache`|可选 `Boolean` 参数。<br /><br /> 如果为 `true`，则将返回缓存的结果（如果存在）。  如果运行 theMSBuild 任务，其结果会被缓存在范围（ProjectFileName、GlobalProperties）\[TargetNames\] 内<br /><br /> 以生成项列表形式|  
  
## 备注  
 除了上面列出的参数，此任务还将从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，此类本身从 <xref:Microsoft.Build.Utilities.Task> 类继承。  有关这些附加参数及其说明的列表，请参见 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
 与使用 [Exec 任务](../msbuild/exec-task.md)启动 MSBuild.exe 不同，此任务使用同一个 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 进程来生成子项目。  可以跳过的已生成目标列表在父生成进程与子生成进程之间共享。  此外，此任务的速度更快，因为它不创建任何新的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 进程。  
  
 此任务不但可以处理项目文件，而且还可以处理解决方案文件。  
  
 即使配置涉及远程基础结构（例如，端口、协议、超时、重试等），也必须通过使用配置文件使 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 为了可以同时生成项目而需要的任何配置变得可配置。  如果可能，应该能够将配置项指定为 `MSBuild` 任务中的任务参数。  
  
 从 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 开始，解决方案项目现在可从它生成的所有子项目中显示 TargetOutputs。  
  
## 向项目传递属性  
 在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 之前的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 版本中，很难向 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项中列出的不同项目传递一系列不同的属性。  如果使用 [MSBuild Task](../msbuild/msbuild-task.md)的 Properties 特性，则其设置将应用于生成的所有项目，除非分批处理 [MSBuild Task](../msbuild/msbuild-task.md)并有条件地为项列表中的每个项目提供不同属性。  
  
 但是，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 提供了两个新的保留元数据项：Properties 和 AdditionalProperties，您可以通过这两个元数据项灵活地向使用 [MSBuild Task](../msbuild/msbuild-task.md)生成的不同项目传递不同的属性。  
  
> [!NOTE]
>  这些新的元数据项只适用于在 [MSBuild Task](../msbuild/msbuild-task.md)的 Projects 特性中传递的项。  
  
## 多处理器生成的优点  
 在多处理器系统中并行生成项目时，使用这一新元数据的一个主要优点便会显现出来。  通过该元数据，可将所有项目都合并到一个 [MSBuild Task](../msbuild/msbuild-task.md)调用中，而无需执行任何批处理或条件 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务。  在只调用一个 [MSBuild Task](../msbuild/msbuild-task.md)时，Projects 特性中列出的所有项目都将并行生成。  （但仅当 [MSBuild Task](../msbuild/msbuild-task.md)中存在 `BuildInParallel=true` 特性时，才会出现上述情况。）有关更多信息，请参见[并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。  
  
## Properties 元数据  
 一种常见的情况是使用 [MSBuild Task](../msbuild/msbuild-task.md)只通过不同的生成配置来生成多个解决方案文件。  您可能要使用“调试”配置生成解决方案 a1，使用“发布”配置生成解决方案 a2。  在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 中，此项目文件将类似于以下内容：  
  
> [!NOTE]
>  在下面的示例中，“...”表示其他解决方案文件。  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 但是，通过使用 Properties 元数据，可将此简化为只使用一个 [MSBuild Task](../msbuild/msbuild-task.md)，如下所示：  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- 或 \-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## AdditionalProperties 元数据  
 请考虑使用 [MSBuild Task](../msbuild/msbuild-task.md)生成两个解决方案文件的情况，两个文件都使用“发布”配置，但其中一个文件使用 x86 体系结构，另一个文件使用 ia64 体系结构。  在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 中，您将需要创建 [MSBuild Task](../msbuild/msbuild-task.md)的多个实例：一个实例将“发布”配置与 x86 体系结构结合使用来生成项目，另一个实例则将“发布”配置与 ia64 体系结构结合使用。  您的项目文件将类似于以下内容：  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 通过使用 AdditionalProperties 元数据，可将此操作简化为只使用一个 [MSBuild Task](../msbuild/msbuild-task.md)，如下所示：  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## 示例  
 下面的示例使用 `MSBuild` 任务来生成 `ProjectReferences` 项集合指定的项目。  生成的目标输出存储在 `AssembliesBuiltByChildProjects` 项集合中。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## 请参阅  
 [任务](../msbuild/msbuild-tasks.md)   
 [任务参考](../msbuild/msbuild-task-reference.md)