---
title: "Folder 元素 （Visual Studio 项目模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords: Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 677b705015b2b12ee484db7595d6cfd919ad61d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder 元素（Visual Studio 项目模板）
指定将添加到项目的文件夹。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<文件夹 >  
  
## <a name="syntax"></a>语法  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`Name`|必需的特性。<br /><br /> 项目文件夹的名称。|  
|`TargetFolderName`|可选特性。<br /><br /> 指定要为文件夹提供从模板创建项目时的名称。 此属性可用于使用参数替换创建的文件夹名称或命名的文件夹的国际字符串都不能直接在.zip 文件中。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|`Folder`|指定要添加到项目的文件夹。 `Folder`元素可以包含子`Folder`元素。|  
|[项目项](../extensibility/projectitem-element-visual-studio-item-templates.md)|指定要向项目中添加的文件。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[项目](../extensibility/project-element-visual-studio-templates.md)|可选子元素[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)。|  
  
## <a name="remarks"></a>备注  
 `Folder`是的可选子`Project`。  
  
 你可以使用任何以下方法将项目项组织到模板中的文件夹：  
  
-   在模板的.zip 文件，包括文件夹并将其添加到项目的.vstemplate 文件中通过指定到中的文件的路径`ProjectItem`元素，没有`Folder`元素。 这是建议的方法。 例如:   
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   在模板的.zip 文件，包括文件夹并将其添加到项目中包含的.vstemplate 文件`Folder`元素。 例如:   
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   在模板.zip 文件中，不包括文件夹，但将使用的文件夹添加`TargetFileName`属性`ProjectItem`元素。 例如:   
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>示例  
 下面的示例演示用于的项目模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows 应用程序。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)