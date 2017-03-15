---
title: "SupportsCodeSeparation 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation> 元素 [Visual Studio 模板]"
  - "SupportsCodeSeparation 元素 [Visual Studio 模板]"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SupportsCodeSeparation 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定是否在**“添加新项”**对话框中启用**“将代码放在单独的文件中”**复选框。  
  
## 语法  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必需的元素。<br /><br /> 将此模板分类并定义此模板在**“新建项目”**或**“新建项”**对话框中的显示方式。|  
  
## 文本值  
 需要一个文本值。  
  
 此文本必须是 `true` 或 `false`，指示是否在**“添加新项”**对话框中启用**“将代码放在单独的文件中”**复选框。  
  
## 备注  
 `SupportsCodeSeparation` 是可选元素。  默认值为 `false`。  
  
 `SupportsCodeSeparation` 元素只可用于 Web 项模板。  
  
 代码分隔或代码隐藏页模型允许您将标记保存在一个文件中，而将编程代码保存在另一个文件中。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 和其他 .NET 语言使用此模型。  
  
## 示例  
 下面的示例指定要显示**“将代码放在单独的文件中”**选项。  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
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
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)