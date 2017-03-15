---
title: "Folder 元素（Visual Studio 项目模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder 元素 [Visual Studio 项目模板]"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Folder 元素（Visual Studio 项目模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定将添加到项目中的文件夹。  
  
## 语法  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`Name`|必需的特性。<br /><br /> 项目文件夹的名称。|  
|`TargetFolderName`|可选特性。<br /><br /> 指定当从模板创建项目时给定的文件夹名称。  当使用参数替换来创建文件夹名称时，或者当使用不能在 .zip 文件中直接使用的国际字符串来命名文件夹时，此特性非常有用。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|`Folder`|指定要添加到此项目的文件夹。  `Folder` 元素可包含子 `Folder` 元素。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|指定要添加到项目中的文件。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[项目](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md) 的可选子元素。|  
  
## 备注  
 `Folder` 是 `Project` 的可选子级。  
  
 可以使用以下任何一种方法将项目项组织到某个模板的各个文件夹中：  
  
-   将这些文件夹包括在模板的 .zip 文件中，然后在 `ProjectItem` 元素中指定文件的路径，从而将这些文件夹添加到 .vstemplate 文件中的此项目里，此处不使用 `Folder` 元素。  此方法为建议采用的方法。  例如：  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   将这些文件夹包括在模板的 .zip 文件中，然后使用 `Folder` 元素将这些文件夹添加到 .vstemplate 文件中的此项目里。  例如：  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   不将文件夹包括在模板的 .zip 文件中，但使用 `ProjectItem` 元素的 `TargetFileName` 特性添加文件夹。  例如：  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## 示例  
 下面的示例演示针对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 应用程序的某个项目模板的元数据。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)