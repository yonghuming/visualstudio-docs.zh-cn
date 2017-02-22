---
title: "RequiredPlatformVersion 元素（Visual Studio 模板） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# RequiredPlatformVersion 元素（Visual Studio 模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定项目模板正常工作所需的操作系统的最低版本。 此元素还用于创建的项目模板 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 应用程序。  
  
 `RequiredPlatformVersion` 值直接与操作系统的版本进行比较。 如果 `RequiredPlatformVersion` 高于操作系统版本中未显示模板 **新项目** 对话框。 若要指定为模板 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更高版本，请设置 `RequiredPlatformVersion` 到 6.2.0。 若要指定为模板 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 或更高版本，请设置 RequiredPlatformVersion 为 6.3.0。  
  
 指定模板 `RequiredPlatformVersion`\= 8 都与以前的客户兼容 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 模板。  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
RequiredPlatformVersion  
  
## 语法  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## 特性和元素  
 无。  
  
### 特性  
 无。  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|指定项目模板面向的平台。|  
  
## 文本值  
 需要一个文本值。  
  
## 备注  
 此文本指定模板所需的最低操作系统版本。  
  
## 示例  
 此示例指定项目模板面向 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或更高版本。  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [TargetPlatformName 元素（Visual Studio 模板）](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)