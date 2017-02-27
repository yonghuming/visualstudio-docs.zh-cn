---
title: "目标生成顺序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, 生成顺序"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 目标生成顺序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果一个目标的输入取决于另一个目标的输出，则必须对目标进行排序。  可以使用这些属性指定目标的运行顺序：  
  
-   `InitialTargets`.  此 `Project` 属性指定将首先运行的目标，因此，即使在命令行或在 `DefaultTargets` 属性。  
  
-   `DefaultTargets`.  此 `Project` atttribute 指定哪些目标运行，如果目标没有在命令行显式指定。  
  
-   `DependsOnTargets`.  此 `Target` 属性指定必须运行的目标，此目标然后才能运行。  
  
-   `BeforeTargets` 和 `AfterTargets`。  这些 `Target` 属性指定此目标应当在指定的目标 \(MSBuild 4.0\) 之前或之后运行。  
  
 一个目标决不会在生成过程中运行两次，即便生成中后面的目标依赖于它也是如此。  一个目标运行之后，它对相应生成的作用亦即完成。  
  
 目标可能有 `Condition` 特性。  如果指定条件的计算结果为 `false`，则不执行目标并且对生成没有影响。  有关条件的更多信息，请参见 [条件](../msbuild/msbuild-conditions.md)。  
  
## 初始目标  
 [项目](../msbuild/project-element-msbuild.md) 元素的 `InitialTargets` 属性指定将首先运行的目标，因此，即使在命令行或在 `DefaultTargets` 属性。  初始目标通常用于错误检查。  
  
 `InitialTargets` 属性的值可以是分号分隔，有序列表目标。  下面的示例指定 `Warm` 目标运行，`Eject` 目标再运行。  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 导入的项目可能有自己的 `InitialTargets` 特性。  所有初始目标都聚合在一起，并按顺序运行。  
  
 有关更多信息，请参见[如何：指定首先生成的目标](../msbuild/how-to-specify-which-target-to-build-first.md)。  
  
## 默认目标  
 [项目](../msbuild/project-element-msbuild.md) 元素的 `DefaultTargets` 属性指定哪些目标或目标生成，如果目标没有在命令行显式指定。  
  
 `DefaultTargets` 属性的值可以是分号分隔，有序列表默认值目标。  下面的示例指定 `Clean` 目标运行，`Build` 目标再运行。  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 您可以重写默认值目标使用 **\/target** 命令行开关。  下面的示例指定 `Build` 目标运行，`Report` 目标再运行。  在此类时指定目标，所有默认值目标被忽略。  
  
 `msbuild /target:Build;Report`  
  
 如果两个初始目标和默认值，指定目标，并且，如果未指定任何命令行目标，则 MSBuild 将先运行初始目标，然后运行默认值目标。  
  
 导入的项目可能有自己的 `DefaultTargets` 特性。  遇到的第一个 `DefaultTargets` 特性确定哪个默认目标将运行。  
  
 有关更多信息，请参见[如何：指定首先生成的目标](../msbuild/how-to-specify-which-target-to-build-first.md)。  
  
## 第一个目标  
 如果没有初始目标、默认目标或命令行目标，则 MSBuild 将先运行它在项目文件或任何导入的项目文件中遇到的第一个目标。  
  
## 目标依赖项  
 目标可以描述相互之间的依存关系。  `DependsOnTargets` 特性指示某个目标依赖于其他目标。  例如，  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 通知 MSBuild `Serve` 目标依赖于 `Chop` 目标和 `Cook` 目标。  在运行 `Serve` 目标之前，MSBuild 运行 `Chop` 目标，然后运行 `Cook` 目标。  
  
## 在目标之前和在目标之后  
 在 MSBuild 4.0 中，可以使用 `BeforeTargets` 和 `AfterTargets` 特性指定目标顺序。  
  
 请看下面的脚本。  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 若要创建在 `Compile` 目标的中间请在 `Link` 目标之前面向 `Optimize`，但，添加以下目标中的任意位置 `Project` 元素。  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## 确定目标生成顺序  
 MSBuild 按如下方式确定目标生成顺序：  
  
1.  `InitialTargets` 目标运行。  
  
2.  运行通过 **\/target** 开关在命令行上指定的目标。  如果在命令行上未指定目标，则 `DefaultTargets` 目标运行。  如果两者均不存在，则遇到的第一个目标运行。  
  
3.  计算目标的 `Condition` 特性。  如果 `Condition` 属性存在并且计算结果为 `false`，则不执行目标并且对生成没有进一步的影响。  
  
4.  在执行目标之前，将运行其 `DependsOnTargets` 目标。  
  
5.  在执行目标之前，将运行在 `BeforeTargets` 特性中列出该目标的任何目标。  
  
6.  在执行目标之前，将比较其 `Inputs` 特性和 `Outputs` 特性。  如果 MSBuild 确定任何输出文件已过时有关对应的输入文件，则 MSBuild 将执行目标。  否则，MSBuild 将跳过目标。  
  
7.  执行或跳过目标之后，将运行在 `AfterTargets` 特性中列出该目标的任何目标。  
  
## 请参阅  
 [目标](../msbuild/msbuild-targets.md)