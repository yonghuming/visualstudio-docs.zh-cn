---
title: "NumberOfParentCategoriesToRollUp（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp"
helpviewer_keywords: 
  - "<NumberOfParentCategoriesToRollUp> 元素 [Visual Studio 模板]"
  - "NumberOfParentCategoriesToRollUp 元素 [Visual Studio 模板]"
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# NumberOfParentCategoriesToRollUp（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定将在**“新建项目”**对话框中显示此模板的父类别的数目。  
  
## 语法  
  
```  
<NumberOfParentCategoriesToRollUp>  
    1  
</NumberOfParentCategoriesToRollUp>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|将此模板分类并定义此模板在**“新建项目”**或**“添加新项”**对话框中的显示方式。|  
  
## 文本值  
 需要一个 `integer` 值。  
  
 该值指定将在**“新建项目”**对话框中显示此模板的父类别的数目。  
  
## 备注  
 `NumberOfParentCategoriesToRollUp` 是可选元素。  
  
## 示例  
 此示例演示 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 应用程序的元数据。  如果具有此元数据的模板放置在低于顶级 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 节点两个文件夹级别的位置上，则该模板将出现在**“新建项目”**对话框中的顶级节点中。  如果没有设置 `NumberOfParentCategoriesToRollUp`，则该模板仅出现在它实际位于的节点中。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
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