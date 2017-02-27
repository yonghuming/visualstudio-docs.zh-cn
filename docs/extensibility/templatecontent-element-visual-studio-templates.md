---
title: "TemplateContent 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent"
helpviewer_keywords: 
  - "TemplateContent 元素 [Visual Studio 项目模板]"
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# TemplateContent 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定模板的内容。  
  
## 语法  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|指定从此模板创建项目时是否生成解决方案。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定多项目模板的组织和内容。|  
|[项目](../extensibility/project-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定要添加到项目中的文件或目录。|  
|[引用](../extensibility/references-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定某个项模板所需的程序集引用。|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|可选元素。<br /><br /> 指定包含在此模板中的文件。|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定的任何自定义参数，在项目或项从模板中创建。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必需的元素。<br /><br /> 包含项目模板、项模板或初学者工具包的所有元数据。|  
  
## 备注  
 `TemplateContent` 是必选元素。  
  
## 示例  
 下面的示例演示针对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 应用程序的某个项目模板的元数据。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)