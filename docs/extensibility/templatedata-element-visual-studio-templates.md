---
title: "TemplateData 元素 （Visual Studio 模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 185734d82820c8de0d84e995e2ff88894a2c86dc
ms.lasthandoff: 02/22/2017

---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 元素（Visual Studio 模板）
将此模板分类并定义此模板在 **“新建项目”** 或 **“添加新项”** 对话框中的显示方式。  
  
 \<VSTemplate&1;>  
 \<TemplateData&1;>  
  
## <a name="syntax"></a>语法  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|必需的元素。<br /><br /> 指定模板的名称出现在**新项目**或**添加新项**对话框。|  
|[描述](../extensibility/description-element-visual-studio-templates.md)|必需的元素。<br /><br /> 指定模板的说明中任意一种出现**新项目**或**添加新项**对话框。|  
|[图标](../extensibility/icon-element-visual-studio-templates.md)|必需的元素。<br /><br /> 指定的路径和用作该图标，将出现在任何一个图像文件的文件名**新项目**或**添加新项**对话框中，为该模板。|  
|[项目类型](../extensibility/projecttype-element-visual-studio-templates.md)|必需的元素。<br /><br /> 将项目模板分类以使其显示在指定组下**新项目**对话框。|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|可选元素。<br /><br /> 将分类的项目模板，使其出现在中指定的子类别下**新项目**对话框。|  
|[模板 Id](../extensibility/templateid-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定模板 id。|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定模板组 id。|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定一个值，用于排列，该模板后，同一类别中的其他模板之间出现在任何一个**新项目**或**添加新项**对话框。|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定是否在项目的实例化时创建包含文件夹。|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|可选元素。<br /><br /> 创建时指定 Visual Studio 项目系统将生成项目或项的名称。|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定是否创建它时，Visual Studio 项目系统将生成项目或项的默认名称。|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定是否可以为临时项目创建项目。|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定是否**浏览**提供了按钮**新项目**对话框中，以便用户可以轻松地修改保存一个新的项目的默认目录。|  
|[隐藏](../extensibility/hidden-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定模板是否出现在**新项目**或**添加新项**对话框。|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|可选元素。<br /><br /> 指定将显示在此模板的父类别数**新项目**对话框。|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|可选元素。|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|可选元素。<br /><br /> 指定是否**位置**文本框中**新项目**对话框中可以启用、 禁用，或隐藏的项目模板。|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|可选元素。<br /><br /> 如果该模板仅支持特定的最低版本和更高版本，如果任何.NET Framework，请使用此元素。|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定模板是否支持 web 项目母板页。|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定是否模板支持代码分离或代码隐藏页模型，用于 web 项目。|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定该模板是相同的多个语言，以及是否**语言**中将提供选项**新项目**对话框。|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|可选元素。<br /><br /> 指定项目模板面向的平台。 此元素指定的项目模板用于创建[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]应用程序。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必需的元素。<br /><br /> 包含项目模板、 项模板或初学者工具包的所有元数据。|  
  
## <a name="remarks"></a>备注  
 `TemplateData`是必需的元素。  
  
 如果不包括可选元素，则使用该元素的默认值。  
  
## <a name="example"></a>示例  
 下面的示例演示一个用于项目模板的元数据[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]应用程序。  
  
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
