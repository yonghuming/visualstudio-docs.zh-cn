---
title: "ProjectType 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords: ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb177139491236cf518aba4e7f2effd213c1a469
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType 元素（Visual Studio 模板）
将项目模板的分类，以使其显示在指定的组下**新项目**或**添加新项**对话框。  
  
> [!WARNING]
>  启动 Visual Studio 2012 中的 c + + 支持项目模板。 不支持 Visual Studio 2010 和早期版本中的 c + +。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>语法  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|将此模板分类并定义此模板在 **“新建项目”** 或 **“添加新项”** 对话框中的显示方式。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 此值指定类型的项目模板将创建，并且必须包含以下值之一：  
  
-   `CSharp`： 指定该模板创建了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]项目或项。  
  
-   `VisualBasic`： 指定该模板创建了[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]项目或项。  
  
-   `Web`： 指定此模板创建的 Web 项目。 如果`ProjectType`元素包含此值，在定义的项目或项的语言[ProjectSubType 元素 （Visual Studio 模板）](../extensibility/projectsubtype-element-visual-studio-templates.md)。  
  
## <a name="remarks"></a>备注  
 `ProjectType` 是 `TemplateData` 的必需子元素。  
  
 值`ProjectType`元素指定在其中提供了该模板**新项目**或**添加新项**对话框。 例如，具有的模板`ProjectType`值`CSharp`下显示**Visual C#**中的节点**新项目**对话框。  
  
 可以通过使用指定的模板子类型[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)元素。  
  
## <a name="example"></a>示例  
 下面的示例演示用于的项目模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]应用程序。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建项目和项模板](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType 元素（Visual Studio 模板）](../extensibility/projectsubtype-element-visual-studio-templates.md)