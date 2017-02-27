---
title: "ProvideDefaultName 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName 元素 [Visual Studio 项目模板]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# ProvideDefaultName 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目系统是否将为**“添加新项”**或**“新建项目”**对话框中的模板生成默认名称。  
  
## 语法  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 此文本必须是 `true` 或 `false`，以指示是否为**“添加新项”**或**“新建项目”**对话框中的模板生成默认名称。  
  
## 备注  
 `ProvideDefaultName` 是可选元素。  默认值为 `true`。  
  
 如果 `ProvideDefaultName` 元素为 `false`，则**“添加新项”**和**“新建项目”**对话框中的**“名称”**框包含值 `<Enter_name>`。  
  
 使用 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) 元素指定**“添加新项”**和**“新建项目”**对话框中的项目或项的默认名称。  
  
## 示例  
 下面的代码示例将 `ProvideDefaultName` 元素设置为 `false`。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)