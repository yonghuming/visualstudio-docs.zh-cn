---
title: "MSBuild 目标 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 目标"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# MSBuild 目标
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

目标以特定的顺序将任务组合到一起，并允许生成过程分解为较小的单位。  例如，一个目标可能会删除输出目录中的所有文件以准备进行生成，而另一个目标可能会编译项目的输入并将它们放到该空目录中。  有关任务的更多信息，请参见 [任务](../msbuild/msbuild-tasks.md)。  
  
## 在项目文件中声明目标  
 目标是使用 [Target](../msbuild/target-element-msbuild.md) 元素在项目文件中声明的。  例如，下面的 XML 创建一个名为 Construct 的目标，然后，该目标对 Compile 项类型调用 Csc 任务。  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 像 MSBuild 属性一样，目标可以重新定义。  例如，  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 如果 AfterBuild 执行，则仅显示“第二次出现”。  
  
## 目标生成顺序  
 如果一个目标的输入取决于另一个目标的输出，则必须对目标进行排序。  可以通过多种方法指定目标的运行顺序。  
  
-   初始目标  
  
-   默认目标  
  
-   第一个目标  
  
-   目标依赖项  
  
-   `BeforeTargets` 和 `AfterTargets` \(MSBuild 4.0\)  
  
 目标决不会在一个生成过程中运行两次，即便生成中后面的目标依赖于它也是如此。  目标运行之后，它对生成的作用亦即完成。  
  
 有关目标生成顺序的详细信息和更多信息，请参见[目标生成顺序](../msbuild/target-build-order.md)。  
  
## 目标批处理  
 目标元素可能具有 `Outputs` 特性，该特性指定 %\(元数据\) 形式的元数据。  如果是这样，MSBuild 将针对每个唯一元数据值运行一次目标，并对具有该元数据值的项进行分组或“批处理”。  例如，  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 按 Reference 项的 RequiredTargetFramework 元数据对 Reference 项进行批处理。  目标的输出如下所示：  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 实际生成中很少使用目标批处理。  任务批处理更为常见。  有关更多信息，请参见[批处理](../msbuild/msbuild-batching.md)。  
  
## 增量生成  
 增量生成已经过优化，这样，如果目标所具有的输出文件相对于其对应的输入文件而言是最新的，则该目标不会执行。  目标元素既可以具有 `Inputs` 特性（指明目标预计作为输入的项），也可以具有 `Outputs` 特性（指明目标作为输出所生成的项）。  
  
 如果所有输出项都是最新的，则 MSBuild 将跳过目标，这可以显著加快生成速度。  这称为目标的增量生成。  如果只有部分文件为最新，则 MSBuild 将执行目标，但会跳过最新的项。  这称为目标的部分增量生成。  有关更多信息，请参见[增量生成](../msbuild/incremental-builds.md)。  
  
## 请参阅  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [如何：在多个项目文件中使用同一目标](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)