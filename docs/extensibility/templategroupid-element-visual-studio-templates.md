---
title: "TemplateGroupID 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> 元素 [Visual Studio 模板]"
  - "TemplateGroupID 元素 [Visual Studio 模板]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# TemplateGroupID 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定项模板将显示在哪种项目类型中。  当将 [ShowByDefault（Visual Studio 模板）](../extensibility/showbydefault-visual-studio-templates.md)设置为 `false` 时，此元素很重要。  当将 [ShowByDefault（Visual Studio 模板）](../extensibility/showbydefault-visual-studio-templates.md)设置为 `true` 后，项模板将在所有项目类型中可用。  
  
## 语法  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|将此模板分类并定义此模板在**“新建项目”**或**“添加新项”**对话框中的显示方式。|  
  
## 文本值  
 需要一个文本值。  
  
 此文本指定项模板类别的标识符。  
  
## 备注  
 `TemplateGroupID` 是一个元素。  
  
 `TemplateGroupID` 元素的值与项目系统注册 \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<version number\>*\\Projects\\\) 结合使用以筛选在**“添加新项”**对话框中显示的模板。  
  
|Visual C\+\+ 值|含义|  
|--------------------|--------|  
|VC\-Native|用于本机项目。  如果无法确定项目类型，也可以用于默认项目。|  
|VC\-Managed|用于托管 \(\/clr\) 项目|  
|VC\-Windows|用于面向 Windows 平台（本机\/托管\/应用商店）的所有项目|  
|WinRT\-Native\-UAP|用于 Windows 10 应用商店项目|  
|CodeSharing\-Native|用于共享项项目|  
|WinRT\-Native\-6.3|用于 Windows 8.1 应用商店项目|  
|WinRT\-Native\-Phone\-6.3|用于 Windows Phone 8.1 项目|  
|WinRT\-Native|用于 Windows 8.0 应用商店项目|  
|VC\-Android|用于 Android 项目|  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)