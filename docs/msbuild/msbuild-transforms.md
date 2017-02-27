---
title: "MSBuild 转换 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 转换"
  - "转换 [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# MSBuild 转换
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

转换是从一个项列表到另一个项列表的一对一变换。  通过转换，不仅项目可以转换项列表，而且目标还可以标识其输入和输出之间的直接映射。  本主题介绍转换以及 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 如何使用转换来更高效地生成项目。  
  
## 转换修饰符  
 转换不是任意的，而是受特殊语法的限制，其中所有的转换修饰符必须采用 %\(*项元数据名称*\) 的格式。  任何项元数据都可以用作转换修饰符。  这包括在创建每一项时为其分配的已知项元数据。  有关已知项元数据的列表，请参见 [常见的项元数据](../msbuild/msbuild-well-known-item-metadata.md)。  
  
 在下面的示例中，将一个 .resx 文件列表转换为一个 .resources 文件列表。  %\(filename\) 转换修饰符指定各个 .resources 文件与对应的 .resx 文件具有相同的文件名称。  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  您可以为转换后的项列表指定自定义分隔符，就像为标准项列表指定分隔符一样。  例如，要使用逗号 \(,\) 而不是默认的分号 \(;\) 来分隔转换后的项列表，请使用下面的 XML。  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 例如，如果 @\(RESXFile\) 项列表中的项为 `Form1.resx`、`Form2.resx` 和 `Form3.resx`，则转换后的列表中的输出将为 `Form1.resources`、`Form2.resources` 和 `Form3.resources`。  
  
## 使用多个修饰符  
 转换表达式可以包含多个修饰符，这些修饰符可按任何顺序组合，并且可以重复使用。  在下面的示例中，包含文件的目录的名称进行了更改，但是文件保留原来的名称和文件扩展名。  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 例如，如果 `RESXFile` 项列表中包含的项为 `Project1\Form1.resx`、`Project1\Form2.resx` 和 `Project1\Form3.text`，则转换后的列表中的输出将为 `Toolset\Form1.resx`、`Toolset\Form2.resx` 和 `Toolset\Form3.text`。  
  
## 依赖项分析  
 转换可保证在转换后的项列表与原始项列表之间存在一对一的映射关系。  因此，如果目标创建的输出是输入的转换，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 就可以分析输入和输出的时间戳，确定是要跳过、生成还是部分重新生成目标。  
  
 在以下示例的[Copy 任务](../msbuild/copy-task.md)中，`BuiltAssemblies` 项列表中的每个文件都映射到该任务的目标文件夹（由 `Outputs` 特性中的转换指定）中的某个文件。  如果 `BuiltAssemblies` 项列表中的文件发生更改，将仅为发生更改的文件运行 `Copy` 任务，而跳过所有其他文件。  有关依赖关系分析及如何使用转换的更多信息，请参见[如何：增量生成](../msbuild/how-to-build-incrementally.md)。  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## 示例  
  
### 说明  
 下面的示例演示一个使用转换的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件。  此示例假定 c:\\sub0\\sub1\\sub2\\sub3 目录中仅有一个 .xsd 文件，并假定工作目录为 c:\\sub0。  
  
### 代码  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### 注释  
 该示例产生下面的输出。  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## 请参阅  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild 参考](../msbuild/msbuild-reference.md)   
 [如何：增量生成](../msbuild/how-to-build-incrementally.md)