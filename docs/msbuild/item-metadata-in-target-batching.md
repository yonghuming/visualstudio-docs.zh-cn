---
title: "目标批处理中的项元数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "批处理 [MSBuild]"
  - "MSBuild, 目标批处理"
  - "目标批处理 [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 目标批处理中的项元数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 能够对生成目标的输入和输出执行依赖项分析。  如果确定了目标的输入或输出是最新的，将跳过该目标并继续生成过程。  `Target` 元素使用 `Inputs` 和 `Outputs` 特性来指定在依赖项分析过程中要检查的项。  
  
 如果目标包含使用批处理的项作为输入或输出的任务，该目标的 `Target` 元素应当在其 `Inputs` 特性或 `Outputs` 特性中使用批处理，以便 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 能够跳过已经是最新的项批。  
  
## 批处理目标  
 下面的示例包含一个名为 `Res` 的项列表，该项集合根据 `Culture` 项元数据被划分为两个批。  其中每个批分别传递到 `AL` 任务中，该任务为每个批分别创建一个输出程序集。  通过对 `Target` 元素的 `Outputs` 特性使用批处理，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 可以在运行目标之前确定各个批是否是最新的。  如果不使用目标批处理，在每次执行目标时，任务都会运行这两个项批。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## 请参阅  
 [如何：增量生成](../msbuild/how-to-build-incrementally.md)   
 [批处理](../msbuild/msbuild-batching.md)   
 [Target 元素 \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [任务批处理中的项元数据](../msbuild/item-metadata-in-task-batching.md)