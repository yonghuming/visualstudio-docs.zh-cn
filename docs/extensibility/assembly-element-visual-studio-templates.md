---
title: "Assembly 元素（Visual Studio 模板） | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly 元素 [Visual Studio 模板]"
  - "<Assembly> 元素[Visual Studio 模板]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Assembly 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定与某个程序集相关的信息，模板使用此信息将该程序集的引用添加到项目中。  
  
## 语法  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
 无。  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[引用](../extensibility/reference-element-visual-studio-templates.md)|指定将项添加到某个项目时要添加的程序集引用。|  
  
## 文本值  
 需要一个文本值。  
  
 此文本指定实例化项模板时要添加到某个项目中的程序集。  该程序集的名称必须按以下一种方式指定：  
  
-   作为完整的程序集名称。  例如：  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   作为简单文本引用。  例如：  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## 备注  
 `Assembly` 是 `Reference` 的一个必选子元素。  
  
 `Reference`、`References,` 和 `Assembly` 元素只能用于 `Type` 特性值为 `Item` 的 .vstemplate 文件中。  
  
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