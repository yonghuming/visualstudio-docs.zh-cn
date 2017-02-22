---
title: "MaxFrameworkVersion 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> 元素（Visual Studio 模板）"
  - "MaxFrameworkVersion 元素（Visual Studio 模板）"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# MaxFrameworkVersion 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定模板要求的 .NET Framework 的最高版本。  它基于**“添加新项目”**对话框的**“目标 Framework 版本”**框中选择的值，确定模板是否在**“添加新项目”**对话框的**“模板”**部分中显示。  
  
## 语法  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 文本必须为模板所允许的 .NET Framework 的最高版本号。  
  
## 备注  
 `MaxFrameworkVersion` 是可选元素。  .vstemplate 文件的 `TemplateData` 节的元素被用作**“添加新项目”**对话框中**“模板”**部分的筛选器。  基于**“添加新项目”** 对话框的**“目标 Framework 版本”**框中选择的值，只会显示其的 .NET Framework 需求低于 `MaxFrameworkVersion` 元素值的模板。  `MaxFrameworkVersion` 元素应被忽略，除非是为避免用于较新版本的 .NET Framework 时不慎导致模板无法显示所必需的。  
  
## 示例  
 下面的示例演示标准的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 类模板的元数据。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 在此示例中，该模板所需的由 `MaxFrameworkVersion` 表示的最高版本的 .NET Framework 为 3.5。  只有在**“添加新项目”**对话框的**“目标框架版本”**中选择 3.0 或 3.5 时才会显示以上模板。  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)