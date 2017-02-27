---
title: "SortOrder 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> 元素 [Visual Studio 模板]"
  - "SortOrder 元素 [Visual Studio 模板]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SortOrder 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定一个值，该值用于此模板出现在**“新建项目”**或**“添加新项”**对话框中时在同一类别中的其他模板之间排列此模板。  
  
## 语法  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 一个 `integer`，它表示排序顺序值。  
  
## 备注  
 `SortOrder` 是可选元素。  默认值为 100，并且所有值都必须为 10 的倍数。  
  
 对于用户创建的模板，将忽略 `SortOrder` 元素。  所有用户创建的模板均按字母顺序排序。  
  
 在**“新建项目”**或**“新添加项”**对话框中，排序顺序值低的模板出现在排序顺序值高的模板之前。  
  
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
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 在此示例中，`SortOrder` 元素相对较高。  其他 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 项模板的 `SortOrder` 值很可能低于 `290`，因此在**“新项”**对话框中将出现在此模板之前。  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)