---
title: "ProjectItem 元素 （Visual Studio 项模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 035e698b0b8f34cbbefc665cc96f38a87a812e2d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem 元素（Visual Studio 项模板）
指定项模板中包含的文件。  
  
> [!NOTE]
>  `ProjectItem`元素接受不同的属性，具体取决于模板是针对某个项目或项。 本主题介绍`ProjectItem`项的元素。 有关说明`ProjectItem`元素的项目模板，请参阅[ProjectItem 元素 （Visual Studio 项目模板）](../extensibility/projectitem-element-visual-studio-project-templates.md)。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`SubType`|可选特性。<br /><br /> 多文件项模板中指定项的子类型。 此值用于确定编辑器，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将用于打开该项目。|  
|`CustomTool`|可选特性。<br /><br /> 条目设置项的项目文件中。|  
|`ItemType`|可选特性。<br /><br /> 设置项 ItemType 项目文件中。|  
|`ReplaceParameters`|可选特性。<br /><br /> 一个布尔值，指定项是否可以从模板创建项目时，必须将其替换的参数值。 默认值是 `false`。|  
|`TargetFileName`|可选特性。<br /><br /> 指定从模板创建的项目的名称。 此属性可用于使用参数替换创建项名称。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|指定模板的内容。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 A `string` ，它表示.zip 模板文件中的文件的名称。  
  
## <a name="remarks"></a>备注  
 `ProjectItem`是的可选子`TemplateContent`。  
  
 `TargetFileName`属性可以用于重命名文件使用的参数。 例如，如果该文件`MyFile.vb`位于根目录下的模板的.zip 文件，但你想要将名为的文件根据用户在提供的文件名称**添加新项**对话框中，你将使用下面的 XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 文件名称时从该模板创建一个项，将基于用户输入中的名称**添加新项**对话框。 创建多文件项模板时，这很有用。 有关详细信息，请参阅[如何： 创建多文件项模板](../ide/how-to-create-multi-file-item-templates.md)和[模板参数](../ide/template-parameters.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示的标准项模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]类。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [如何：创建多文件项模板](../ide/how-to-create-multi-file-item-templates.md)   
 [模板参数](../ide/template-parameters.md)