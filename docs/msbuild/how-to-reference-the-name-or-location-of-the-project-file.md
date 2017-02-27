---
title: "如何：引用项目文件的名称或位置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "引用的位置"
  - "位置"
  - "MSBuildProjectName 属性"
  - "MSBuild，引用项目文件"
  - "引用的名称"
  - "保留属性"
  - "引用的项目文件"
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>如何：引用项目文件的名称或位置
可以在项目文件自身中使用该项目的名称或位置，而无需创建你自己的属性。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供引用项目文件名的保留属性和与项目相关的其他属性。 有关保留属性的详细信息，请参阅 [MSBuild 保留属性和常见属性](../msbuild/msbuild-reserved-and-well-known-properties.md)。  
  
## <a name="using-the-msbuildprojectname-property"></a>使用 MSBuildProjectName 属性  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供一些可以在项目文件中使用而无需每次都对其进行定义的保留属性。 例如，保留属性 `MSBuildProjectName` 提供对项目文件名的引用。  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>使用 MSBuildProjectName 属性  
  
-   使用 $() 表示法在项目文件中引用属性，就像引用任何其他属性一样。 例如：  
  
    ```xml  
    <CSC Sources = "@(CSFile)"   
        OutputAssembly = "$(MSBuildProjectName).exe"/>  
    </CSC>  
    ```  
  
 使用保留属性的一个优点是对项目文件名所作的任何更改都将自动纳入。 下次生成项目时，输出文件将具有该新名称，而你不需要执行任何进一步的操作。  
  
> [!NOTE]
>  无法在项目文件中重新定义保留属性。  
  
## <a name="example"></a>示例  
 以下示例项目文件将项目名称作为保留属性引用，以指定输出的名称。  
  
```xml  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>另请参阅  
[MSBuild](../msbuild/msbuild.md)  
 [MSBuild 保留属性和已知属性](../msbuild/msbuild-reserved-and-well-known-properties.md)


<!--HONumber=Feb17_HO4-->


