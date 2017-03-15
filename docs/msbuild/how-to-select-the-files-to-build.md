---
title: "如何：选择要生成的文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Include 特性 [MSBuild]"
  - "MSBuild, 包含文件"
  - "MSBuild, 通配符"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：选择要生成的文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果生成的项目中包含多个文件，则可以在项目文件中分别列出每个文件，也可以使用通配符将一个目录或一组嵌套目录中的所有文件都包括进去。  
  
## 指定输入  
 项表示某个生成的输入。  有关项的更多信息，请参见 [项](../msbuild/msbuild-items.md)。  
  
 若要包括某个生成的文件，必须在 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目文件的项列表中包括这些文件。  通过逐个包括文件或使用通配符同时包括许多文件，可以将多个文件添加到项列表中。  
  
#### 逐个声明各个项  
  
-   使用 `Include` 特性，如下所示：  
  
     `<CSFile Include="form1.cs"/>`  
  
     \- 或 \-  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  如果在项目集合中的项目不在内容和项目文件同名，则必须指定完整路径或相对路径添加到项目中。  例如：`Include="..\..\form2.cs"`。  
  
#### 声明多个项  
  
-   使用 `Include` 特性，如下所示：  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     \- 或 \-  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## 使用通配符指定输入  
 还可以使用通配符以递归方式将子目录中的所有文件或某些特定文件包括在某个生成的输入列表中。  有关通配符的更多信息，请参见 [项](../msbuild/msbuild-items.md)。  
  
 下面的示例基于一个项目，该项目包含下列目录和子目录中的图形文件，项目文件在 Project 目录中：  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### 包括 Images 目录和子目录中的所有 .jpg 文件  
  
-   使用下面的 `Include` 特性：  
  
     `Include="Images\**\*.jpg"`  
  
#### 包括所有以“img”开头的 .jpg 文件  
  
-   使用下面的 `Include` 特性：  
  
     `Include="Images\**\img*.jpg"`  
  
#### 包括名称以“jpgs”结尾的目录中的所有文件  
  
-   使用下列 `Include` 特性之一：  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     \- 或 \-  
  
     `Include="Images\**\*jpgs\*"`  
  
## 将项传递给任务  
 在项目文件中，可以在任务中使用 @\(\) 表示法指定整个项列表作为某个生成的输入。  无论是分别列出所有文件还是使用通配符，都可以使用此表示法。  
  
#### 使用所有 Visual C\# 或 Visual Basic 文件作为输入  
  
-   使用 `Include` 特性，如下所示：  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     \- 或 \-  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  对项来说，必须使用通配符来指定某个生成的输入，不能使用 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 任务（如 [Csc](../msbuild/csc-task.md) 或 [Vbc](../msbuild/vbc-task.md)）中的 `Sources` 特性来指定输入。  下面的示例在项目文件中无效：  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## 示例  
 下面的代码示例显示的项目分别包括所有输入文件。  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## 示例  
 下面的代码示例使用通配符来包括所有 .cs 文件。  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## 请参阅  
 [如何：将文件排除在生成过程外](../msbuild/how-to-exclude-files-from-the-build.md)   
 [项](../msbuild/msbuild-items.md)