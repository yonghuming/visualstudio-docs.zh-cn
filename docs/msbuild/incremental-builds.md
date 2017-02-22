---
title: "增量生成 | Microsoft Docs"
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
  - "msbuild, 增量生成"
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 增量生成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

增量生成已经过优化，这样，如果目标所具有的输出文件相对于其对应的输入文件而言是最新的，则该目标不会执行。  目标元素既可以具有 `Inputs` 特性（指明目标预计作为输入的项），也可以具有 `Outputs` 特性（指明目标作为输出所生成的项）。  MSBuild 将尝试查找这些特性值之间的 1 对 1 映射。  如果存在 1 对 1 映射，则 MSBuild 会将每个输入项的时间戳与其对应输出项的时间戳进行比较。  没有 1 对 1 映射的输出文件将与所有输入文件进行比较。  如果某项的输出文件的时间戳与该项的一个或多个输入文件相同，或与之相比较新，则将该项视为最新。  
  
 如果所有输出项均为最新，则 MSBuild 将跳过目标。  目标的这种增量生成可以显著提高生成速度。  如果只有部分文件为最新，则 MSBuild 将执行目标，但会跳过最新的项，从而使所有项均成为最新项。  这称为“部分增量生成”。  
  
 1 对 1 映射通常由项转换生成。  有关详细信息，请参阅[转换](../msbuild/msbuild-transforms.md)。  
  
 请看下面的目标。  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 系统会将由 `Compile` 项类型表示的文件集复制到备份目录。  备份文件的文件扩展名为 .bak。  如果在 Backup 目标运行后未删除或修改由 `Compile` 项类型表示的文件或对应的备份文件，则会在后面的生成中跳过 Backup 目标。  
  
## 输出推理  
 MSBuild 将比较目标的 `Inputs` 和 `Outputs` 特性，以确定目标是否必须执行。  理想情况下，不管是否执行了关联的目标，增量生成完成后存在的文件集应保持不变。  由于任务所创建或更改的属性和项可能会影响生成，因此 MSBuild 必须推断出其值，即使跳过了影响这些值的目标，情况也是如此。  这称为“输出推理”。  
  
 有三种情况：  
  
-   目标具有计算结果为 `false` 的 `Condition` 特性。  在这种情况下，目标不会运行，并且对生成没有影响。  
  
-   目标具有过时的输出，并且目标已运行以使输出成为最新。  
  
-   目标没有过时的输出，并且已跳过目标。  MSBuild 将计算目标，并对项和属性进行更改，就好像目标已运行一样。  
  
 要支持增量编译，任务必须确保任何 `Output` 元素的 `TaskParameter` 特性值均与任务输入参数相等。  下面是一些示例：  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 此示例将创建属性 Easy，不管是否执行或跳过了目标，该属性的值均为“123”。  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 此示例将创建项类型 Simple，不管是否执行或跳过了目标，该项类型都包含两项：“a.cs”和“b.cs”。  
  
 开始于 MSBuild 3.5 中，将对目标中的项和属性组自动执行输出推理。  无需在目标中执行 `CreateItem` 任务，并且应避免该任务。  此外，只有在要确定目标是否已执行时，才应在目标中使用 `CreateProperty` 任务。  
  
## 确定目标是否已运行  
 由于输出推理的原因，您必须在目标中添加 `CreateProperty` 任务，才能检查属性和项，以便能够确定目标是否已执行。  向目标中添加 `CreateProperty` 任务，并为其指定 `TaskParameter` 为“ValueSetByTask”的 `Output` 元素。  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 此示例将创建属性 CompileRan，并为其指定值 `true`，但只有在目标已执行时才会这样做。  如果跳过了目标，则不会创建 CompileRan。  
  
## 请参阅  
 [目标](../msbuild/msbuild-targets.md)