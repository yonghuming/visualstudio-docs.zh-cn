---
title: "MSBuild 批处理 | Microsoft Docs"
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
  - "MSBuild, 批处理"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild 批处理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 能够根据项元数据将项列表划分为不同的类别或批，并在每批中一次运行一个目标或任务。  
  
## 任务批处理  
 任务批处理使您能够简化项目文件，因为它可以将项列表划分为不同的批并将各个批分别传递到任务中。  这意味着项目文件只需声明任务及其特性一次，但却可以多次运行它。  
  
 通过在一个任务特性中使用 %\(*项元数据名称*\) 表示法，指定让 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 使用任务执行批处理。  下面的示例根据 `Color` 项元数据值将 `Example` 项列表拆分为多个批，并将各个批分别传递给 `MyTask` 任务。  
  
> [!NOTE]
>  如果不在任务特性中的其他位置引用项列表，或者元数据名称可能不明确，则可使用 %\(*项集合.项元数据名称*\) 表示法完全限定用于进行批处理的项元数据值。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 有关更为具体的批处理示例，请参见[任务批处理中的项元数据](../msbuild/item-metadata-in-task-batching.md)。  
  
## 目标批处理  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 在运行目标之前会检查该目标的输入和输出是否是最新的。  如果输入和输出都是最新的，将跳过该目标。  如果目标内的任务使用批处理，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 需要确定项的各个批的输入和输出是否都是最新的。  否则，将在每次命中目标时执行目标。  
  
 下面的示例显示一个 `Target` 元素，该元素包含一个具有 %\(*项元数据名称*\) 表示法的 `Outputs` 特性。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 根据 `Color` 项元数据将 `Example` 项列表拆分为多个批，并分析每一批的输出文件的时间戳。  如果某个批的输出不是最新的，将运行目标。  否则，将跳过该目标。  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 有关目标批处理的其他示例，请参见[目标批处理中的项元数据](../msbuild/item-metadata-in-target-batching.md)。  
  
## 使用元数据的属性函数  
 批处理可由包含元数据的属性函数控制。  例如，  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 使用 <xref:System.IO.Path.Combine%2A> 将根文件夹路径和 Compile 项路径组合在一起。  
  
 属性函数不能出现在元数据值中。  例如，  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 是不允许使用的。  
  
 有关属性函数的更多信息，请参见[属性函数](../msbuild/property-functions.md)。  
  
## 请参阅  
 [ItemMetadata 元素 \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [高级概念](../msbuild/msbuild-advanced-concepts.md)