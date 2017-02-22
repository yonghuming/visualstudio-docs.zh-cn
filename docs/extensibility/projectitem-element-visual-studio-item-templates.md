---
title: "ProjectItem 元素（Visual Studio 项模板） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> 元素 [Visual Studio 项模板]"
  - "ProjectItem 元素 [Visual Studio 项模板]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem 元素（Visual Studio 项模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定项模板中包含的某个文件。  
  
> [!NOTE]
>  `ProjectItem` 元素根据模板是项目的模板还是项的模板，接受不同的特性。  此主题解释了项的 `ProjectItem` 元素。  有关项目模板的 `ProjectItem` 元素的解释，请参见 [ProjectItem 元素（Visual Studio 项目模板）](../extensibility/projectitem-element-visual-studio-project-templates.md)。  
  
## 语法  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`SubType`|可选特性。<br /><br /> 指定多文件项模板中某个项的子类型。  此值用于确定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 用来打开此项的编辑器。|  
|`CustomTool`|可选特性。<br /><br /> 为项目文件中的项设置 CustomTool。|  
|`ItemType`|可选特性。<br /><br /> 为项目文件中的项设置 ItemType。|  
|`ReplaceParameters`|可选特性。<br /><br /> 一个布尔值，该值指定从此模板创建项目时此项是否具有必须被替换的参数值。  默认值为 `false`。|  
|`TargetFileName`|可选特性。<br /><br /> 指定从模板创建的项的名称。  使用参数替换创建项名称时，此特性非常有用。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定模板的内容。|  
  
## 文本值  
 需要一个文本值。  
  
 一个 `string`，它表示模板的 .zip 文件中某个文件的名称。  
  
## 备注  
 `ProjectItem` 是 `TemplateContent` 的可选子级。  
  
 可以使用 `TargetFileName` 特性和参数来重命名文件。  例如，如果文件 `MyFile.vb` 位于 .zip 模板文件的根目录中，但您希望按用户在**“添加新项”**对话框中提供的文件名为此文件命名，此时可以使用下面的 XML：  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 从此模板创建项时，将按用户在**“添加新项”**对话框中输入的名称为此文件命名。  创建多文件项模板时，此功能非常有用。  有关更多信息，请参见[如何：创建多文件项模板](../ide/how-to-create-multi-file-item-templates.md)和[模板参数](../ide/template-parameters.md)。  
  
## 示例  
 下面的示例演示针对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 类的标准项模板的元数据。  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建多文件项模板](../ide/how-to-create-multi-file-item-templates.md)   
 [模板参数](../ide/template-parameters.md)