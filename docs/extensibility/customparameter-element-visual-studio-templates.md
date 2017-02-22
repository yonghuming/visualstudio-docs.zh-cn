---
title: "CustomParameter 元素（Visual Studio 模板） | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters 元素 [Visual Studio 项目模板]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# CustomParameter 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含从模板创建某个项目或项时要使用的自定义参数的名称和值。  
  
## 语法  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|说明|  
|--------|--------|  
|`Name`|必需。  参数的名称。  参数的格式为 $*名称*$。|  
|`Value`|必需。  此参数的替换值。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|当模板向导进行参数替换时，对要传递给模板向导的自定义参数进行分组。|  
  
## 备注  
 如果模板包含 `CustomParameter` 元素，则 `Name` 特性的每个实例都会替换为所创建的项目文件或项文件中的 `Value` 特性。  
  
## 示例  
 下面的示例演示如何在一个模板中使用多个自定义参数。  如果项目或项是使用下面的自定义参数从某个模板创建而成，则将模板文件中 `$color1$` 和 `$color2$` 的所有实例分别替换为 `Red` 和 `Blue`。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## 请参阅  
 [CustomParameters 元素（Visual Studio 模板）](../extensibility/customparameters-element-visual-studio-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)