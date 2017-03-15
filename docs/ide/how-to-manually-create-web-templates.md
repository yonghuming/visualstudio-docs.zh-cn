---
title: "如何：手动创建 Web 模板 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "项目模板 [Visual Studio], Web"
  - "模板 [Visual Studio], Web"
  - "Visual Studio 模板, Web"
  - "Web 模板 [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：手动创建 Web 模板
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

创建 Web 模板与创建其他类型的模板不同。  由于 Web 项目模板出现在**“添加新网站”**对话框中，而 Web 项目项又是按编程语言分类的，因此 .vstemplate 文件必须将模板指定为 Web 模板并标识编程语言。  
  
> [!NOTE]
>  Web 模板必须包含一个通过使用 `Project` 元素的 `File` 特性指定的空 .webproj 文件。  虽然 Web 项目不需要项目文件，但此文件对于 Web 模板正常工作是必需的。  
  
### 手动创建 Web 模板  
  
1.  创建一个 Web 项目。  
  
2.  修改或删除该项目中的文件，或向该项目中添加新文件。  
  
3.  创建一个 XML 文件，并使用 .vstemplate 文件扩展名将此文件保存到项目所在的目录中。  不要将此文件添加到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的项目中。  
  
4.  创作 .vstemplate XML 文件以提供项目模板元数据。  有关更多信息，请参见下一节中的示例。  
  
5.  定位到 .vstemplate 文件中的 `ProjectType` 元素，并将其文本值设置为 `Web`。  
  
6.  在 `ProjectType` 元素之后添加一个 `ProjectSubType` 元素，并将其文本值设置为模板的编程语言。  编程语言可为下列值之一：  
  
    -   CSharp  
  
    -   VisualBasic  
  
     例如：  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  选择模板中的文件（其中包括 .vstemplate 文件），右击选定内容，单击**“发送到”**，然后单击**“压缩\(zipped\)文件夹”**。  所选文件被压缩为一个 .zip 文件。  
  
8.  将 .zip 模板文件置于 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目模板目录中。  默认情况下，此目录为 \\ my documents \\ Visual Studio *版本*\\ my exported templates \\。  
  
## 示例  
 下面的示例演示一个用于 Web 项目模板的基本 .vstemplate 文件。  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)