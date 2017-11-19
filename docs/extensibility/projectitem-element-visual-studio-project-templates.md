---
title: "ProjectItem 元素 （Visual Studio 项目模板） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a9685d00f2df0f6819058106771a278b8494520
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 元素（Visual Studio 项目模板）
指定的项目模板中包含的文件。  
  
> [!NOTE]
>  `ProjectItem`元素接受不同的属性，具体取决于模板是针对某个项目或项。 本主题介绍`ProjectItem`项目模板的元素。 有关说明`ProjectItem`元素项模板，请参阅[ProjectItem 元素 （Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<ProjectItem >  
  
## <a name="syntax"></a>语法  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各部分描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`TargetFileName`|可选特性。<br /><br /> 从模板创建项目时指定的名称和项目项的路径。 此属性是对于在.zip 模板文件中创建的目录结构不同的目录结构，或者使用参数替换创建项名称。|  
|`ReplaceParameters`|可选特性。<br /><br /> 一个布尔值，指定项是否可以从模板创建项目时，必须将其替换的参数值。 默认值是 `false`。|  
|`OpenInEditor`|可选特性。<br /><br /> 一个布尔值，指定是否应在其各自编辑器中打开项目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]时从模板创建一个项目。<br /><br /> `OpenInWebBrowser`和`OpenInHelpBrowser`上具有的项，则忽略属性`OpenInEditor`值`true`。<br /><br /> 默认值为 `false`。|  
|`OpenInWebBrowser`|可选特性。<br /><br /> 一个布尔值，指定此项是否应将打开 Web 浏览器从模板创建项目时。<br /><br /> 可以在 Web 浏览器中打开只有 HTML 文件和本地的项目的文本文件。 外部 Url 无法打开与此属性。<br /><br /> 默认值为 `false`。|  
|`OpenInHelpBrowser`|可选特性。<br /><br /> 一个布尔值，指定从模板创建项目时，是否应在帮助查看器中打开项目。<br /><br /> 只有 HTML 文件和本地的项目的文本文件可以帮助浏览器中打开。 外部 Url 无法打开与此属性。<br /><br /> 默认值为 `false`。|  
|`OpenOrder`|可选特性。<br /><br /> 指定一个数字值，表示将在其各自的编辑器中打开的项的顺序。 所有值都必须为 10 的倍数。 项的更高版本`OpenOrder`首先打开值。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[项目](../extensibility/project-element-visual-studio-templates.md)|指定的文件或要添加到项目目录。|  
  
## <a name="text-value"></a>文本值  
 需要一个文本值。  
  
 A`string`表示到模板的.zip 文件中的文件的名称或路径。  
  
## <a name="remarks"></a>备注  
 `ProjectItem`是的可选子`Project`。  
  
 `TargetFileName`属性可以用于在模板的.zip 文件中创建的目录结构不同的目录结构。 例如，如果该文件`MyFile.vb`.zip 模板文件的根目录中存在但你想要放置在一个名为目录中文件`CustomFiles`在从模板创建的所有项目，你将使用以下 XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName`属性还可以用于重命名文件包含在其文件名中的国际字符。 例如，模板的.zip 文件不能包含 Unicode 字符，文件名，因此必须重命名该文件，它可以压缩为一个.zip 文件之前。 `TargetFileName`特性用于将文件名称设置回原始的 Unicode 文件名称。  
  
 `TargetFileName`属性还可以用于重命名文件使用的参数。 下面的过程解释如何重命名文件`MyFile.vb`，其中存在该模板的.zip 文件，为基于项目名称的文件名称的根目录中。  
  
### <a name="to-rename-files-with-parameters"></a>若要使用参数重命名文件  
  
1.  使用下面的 XML 的.vstemplate 文件中：  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  打开项目文件 (对于.vbproj[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]项目) 在文本编辑器或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
3.  在项目文件中类似于下面的 XML 中找到行：  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  用下列 XML 替换该代码行：  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     文件名称时从该模板创建一个项目，将基于用户输入中的名称**新项目**对话框中，所有不安全字符和删除空格。 有关详细信息，请参阅[模板参数](../ide/template-parameters.md)。  
  
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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [模板参数](../ide/template-parameters.md)   
 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)