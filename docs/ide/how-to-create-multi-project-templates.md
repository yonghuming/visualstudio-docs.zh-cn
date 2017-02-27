---
title: "如何：创建多项目模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "多项目模板"
  - "项目模板, 创建多项目模板"
  - "Visual Studio 模板, 创建多项目模板"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：创建多项目模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

多项目模板用作两个或多个项目的容器。  从**“新建项目”**对话框中创建基于多项目模板的项目时，模板中的每个项目都会添加到解决方案中。  
  
 多项目模板被压缩为一个 .zip 文件，其中必须包括下列项：  
  
-   整个多项目模板的根 .vstemplate 文件。  此根 .vstemplate 文件包含**“新建项目”**对话框中显示的元数据，并指定在何处查找此模板中的项目的 .vstemplate 文件。  此文件必须位于 .zip 文件的根目录处。  
  
-   包含一个完整项目模板所需的文件的一个或多个文件夹。  这包括项目的所有代码文件以及项目的 .vstemplate 文件。  
  
 例如，一个包含两个项目的多项目模板 .zip 文件可以具有下列文件和目录：  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 多项目模板的根 .vstemplate 文件在以下几个方面不同于单一项目模板：  
  
-   `VSTemplate` 元素的 `Type` 特性包含值 `ProjectGroup`。  例如：  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   `TemplateContent` 元素包含一个 `ProjectCollection` 元素，该元素具有一个或多个定义所包含项目的 .vstemplate 文件路径的 `ProjectTemplateLink` 元素。  例如：  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 多项目模板的行为也不同于常规模板。  多项目模板具有下列唯一特征：  
  
-   多项目模板中各个项目的名称不能由**“新建项目”**对话框来分配。  而应使用 `ProjectTemplateLink` 元素的 `ProjectName` 特性来指定每个项目的名称。  有关更多信息，请参见下一节中的第一个示例。  
  
-   多项目模板可以包含用不同语言编写的项目，但只能通过使用 `ProjectType` 元素将整个模板本身放在一个类别中。  
  
### 创建多项目模板  
  
1.  创建要包含在多项目模板中的项目。  
  
2.  为每个项目创建 .vstemplate 文件。  有关更多信息，请参见 [如何：创建项目模板](../ide/how-to-create-project-templates.md)。  
  
3.  创建将包含多项目模板的元数据的根 .vstemplate 文件。  有关更多信息，请参见下一节中的第一个示例。  
  
4.  选择要包括在模板中的文件和文件夹，右击选定内容，单击**“发送到”**，然后单击**“压缩\(zipped\)文件夹”**。  文件和文件夹将被压缩为一个 .zip 文件。  
  
5.  将 .zip 模板文件置于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目模板目录中。  默认情况下，此目录为 \\ my documents \\ Visual Studio *版本*\\ templates \\ ProjectTemplates \\。  
  
## 示例  
 此示例演示一个基本的多项目根 .vstemplate 文件。  在此示例中，模板包含两个项目：`My Windows Application` 和 `My Class Library`。  `ProjectTemplateLink` 元素的 `ProjectName` 特性可为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置要分配给此项目的名称。  如果不存在 `ProjectName` 特性，则会使用 .vstemplate 文件的名称作为项目名称。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 示例  
 此示例使用 `SolutionFolder` 元素将项目分为两组：`Math Classes` 和 `Graphics Classes`。  模板包含四个项目，每个解决方案文件夹中放两个。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [如何：创建项目模板](../ide/how-to-create-project-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder 元素（Visual Studio 模板）](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink 元素（Visual Studio 模板）](../extensibility/projecttemplatelink-element-visual-studio-templates.md)