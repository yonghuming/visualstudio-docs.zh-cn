---
title: "References 元素（Visual Studio 模板） | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#References"
helpviewer_keywords: 
  - "<References> 元素 [Visual Studio 模板]"
  - "References 元素 [Visual Studio 模板]"
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# References 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

对模板添加到项目中的程序集引用进行分组。  
  
## 语法  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[引用](../extensibility/reference-element-visual-studio-templates.md)|必需的元素。<br /><br /> 指定将项添加到某个项目时要添加的程序集引用。  一个 `References` 元素中必须有一个或多个 `Reference` 元素。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定模板的内容。|  
  
## 备注  
 `References` 是 `TemplateContent` 的可选子元素。  
  
 `Reference` 和 `References` 元素只能用于 `Type` 特性值为 `Item` 的 .vstemplate 文件中。  
  
## 示例  
 下面的示例演示一个项模板的 `TemplateContent` 元素。  此 XML 添加对 System.dll 和 System.Data.dll 程序集的引用。  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)