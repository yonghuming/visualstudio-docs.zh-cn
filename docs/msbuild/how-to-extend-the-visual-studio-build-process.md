---
title: "如何：扩展 Visual Studio 生成过程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, DependsOn 属性"
  - "MSBuild, 扩展 Visual Studio 生成"
  - "MSBuild, 重写 DependsOn 属性"
  - "MSBuild, 重写预定义目标"
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：扩展 Visual Studio 生成过程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 生成过程由导入到项目文件中的一系列 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .targets 文件定义。  可以对这些导入文件中的 Microsoft.Common.targets 进行扩展，以便允许您在生成过程的几个点运行自定义任务。  本主题介绍可用于扩展 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 生成过程的两个方法：  
  
-   覆盖 Microsoft.Common.targets 中定义的特定预定义目标。  
  
-   覆盖 Microsoft.Common.targets 中定义的“DependsOn”属性。  
  
## 覆盖预定义的目标  
 Microsoft.Common.targets 文件包含一组预定义的空目标，在生成过程中某些主目标的前后会调用这些空目标。  例如，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 调用主要 `CoreBuild` 目标之前的 `BeforeBuild` 目标，以及 `CoreBuild` 目标之后的 `AfterBuild` 目标。  默认情况下，Microsoft.Common.targets 中的空目标不执行任何操作，但是，您可以在导入 Microsoft.Common.targets 的项目文件中定义所需目标，从而重写目标的默认行为。  通过此方法，您可以使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务加强对生成过程的控制。  
  
#### 覆盖预定义的目标  
  
1.  在 Microsoft.Common.targets 中识别要覆盖的预定义目标。  有关可安全覆盖的目标的完整列表，请参见下表。  
  
2.  在项目文件的末尾定义一个或多个目标，目标后面紧跟着 `</Project>` 标记。  例如：  
  
    ```  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  生成项目文件。  
  
 下表显示了 Microsoft.Common.targets 中可以安全覆盖的所有目标。  
  
|Target Name|说明|  
|-----------------|--------|  
|`BeforeCompile`, `AfterCompile`|在其中的一个目标中插入的任务将在核心编译完成之前或之后运行。  多数自定义在这两个目标之一中完成。|  
|`BeforeBuild`, `AfterBuild`|在其中的一个目标中插入的任务将在生成中的其他内容之前或之后运行。 **Note:**  `BeforeBuild` 和 `AfterBuild` 目标已在多数项目文件末尾的注释中定义。  这样，您就可以轻松地将预先生成事件和后期生成事件添加到项目文件中。|  
|`BeforeRebuild`, `AfterRebuild`|在其中的一个目标中插入的任务将在调用内核重新生成功能之前或之后运行。  在 Microsoft.Common.targets 中目标执行顺序是：`BeforeRebuild`、`Clean`、`Build`、`AfterRebuild`。|  
|`BeforeClean`, `AfterClean`|在其中的一个目标中插入的任务将在调用内核清除功能之前或之后运行。|  
|`BeforePublish`, `AfterPublish`|在其中的一个目标中插入的任务将在调用内核发布功能之前或之后运行。|  
|`BeforeResolveReference`, `AfterResolveReferences`|在其中的一个目标中插入的任务将在解析程序集引用之前或之后运行。|  
|`BeforeResGen`, `AfterResGen`|在其中的一个目标中插入的任务将在生成资源之前或之后运行。|  
  
## 覆盖“DependsOn”属性  
 重写预定义目标是一种扩展生成过程的简便方法，但是，由于 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 是按顺序计算目标定义的，因此，您无法阻止导入您的项目的其他项目重写您已经重写的目标。  例如，当导入所有其他项目之后，生成过程会使用项目文件中定义的最后一个 `AfterBuild` 目标。  
  
 可以覆盖整个 Microsoft.Common.targets 文件的 `DependsOnTargets` 特性中使用的“DependsOn”属性，以防止目标的意外覆盖。  例如，`Build` 目标包含值为 `"$(BuildDependsOn)"` 的 `DependsOnTargets` 特性。  请考虑：  
  
```  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 这一段 XML 代码表示，必须先运行 `BuildDependsOn` 属性中指定的所有目标，然后才能运行 `Build` 目标。  `BuildDependsOn` 属性定义为：  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 可以在项目文件的末尾声明另一个名为 `BuildDependsOn` 的属性，从而对此属性值进行覆盖。  将以前的 `BuildDependsOn` 属性包括在新属性中，便可以将新目标添加到目标列表的开头和结尾。  例如：  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 导入项目文件的项目可以覆盖这些属性，而不会覆盖您已进行的自定义。  
  
#### 覆盖“DependsOn”属性  
  
1.  在 Microsoft.Common.targets 中识别要覆盖的预定义的“DependsOn”属性。  要了解常被覆盖的“DependsOn”属性的列表，请参见下表。  
  
2.  在项目文件末尾定义一个或多个属性的其他实例。  将原始属性（例如 `$(BuildDependsOn)`）包含在新属性中。  
  
3.  在属性定义之前或之后定义自定义目标。  
  
4.  生成项目文件。  
  
### 通常被覆盖的“DependsOn”属性  
  
|属性名|说明|  
|---------|--------|  
|`BuildDependsOn`|希望在整个生成过程之前或之后插入自定义目标时要覆盖的属性。|  
|`CleanDependsOn`|希望清理自定义生成过程的输出时要覆盖的属性。|  
|`CompileDependsOn`|希望在编译步骤之前或之后插入自定义过程时要覆盖的属性。|  
  
## 请参阅  
 [Visual Studio 集成](../msbuild/visual-studio-integration-msbuild.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [.Targets 文件](../msbuild/msbuild-dot-targets-files.md)