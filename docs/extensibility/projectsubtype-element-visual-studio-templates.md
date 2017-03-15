---
title: "ProjectSubType 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> 元素 [Visual Studio 模板]"
  - "ProjectSubType 元素 [Visual Studio 模板]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ProjectSubType 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将模板归入 `ProjectType` 元素中指定的值的子类别。  
  
## 语法  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必需的元素。<br /><br /> 将此模板分类并定义此模板在**“新建项目”**或**“添加新项”**对话框中的显示方式。|  
  
## 文本值  
 需要一个文本值。  
  
 此值指定模板的子类别。  
  
## 备注  
 `ProjectSubType` 是 `TemplateData` 的可选子元素。  
  
 `ProjectSubType` 元素为 [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) 元素提供子类别。  此值可以包括：  
  
-   `SmartDevice-NETCFv1`：指定此模板针对 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 1.0 版。  
  
-   `SmartDevice-NETCFv2`：指定此模板针对 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 2.0 版。  
  
 如果模板包含值为 `Web` 的 `ProjectType` 元素，则 `ProjectSubType` 元素指定此模板的编程语言。  此元素可具有下面的值：  
  
-   `CSharp`：指定此模板创建 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web 项目或项。  
  
-   `VisualBasic`：指定此模板创建 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web 项目或项。  
  
## 示例  
 下面的示例演示针对 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 2.0 版的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 设备应用程序的项目模板的元数据。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [ProjectType 元素（Visual Studio 模板）](../extensibility/projecttype-element-visual-studio-templates.md)