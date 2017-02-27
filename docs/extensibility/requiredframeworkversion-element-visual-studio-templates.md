---
title: "RequiredFrameworkVersion 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<RequiredFrameworkVersion>（Visual Studio 模板）"
  - "RequiredFrameworkVersion（Visual Studio 模板）"
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# RequiredFrameworkVersion 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定模板 .Schema Hierarchy 要求的 .NET Framework 的最低版本。  
  
## 语法  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
  
 文本必须为模板所要求的 .NET Framework 的最低版本号。  
  
## 备注  
 `RequiredFrameworkVersion` 是可选元素。  如果模板仅支持特定的 .NET Framework 最低版本和更高版本（如果有），则使用此元素。  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [面向特定的 .NET Framework 版本](../ide/targeting-a-specific-dotnet-framework-version.md)