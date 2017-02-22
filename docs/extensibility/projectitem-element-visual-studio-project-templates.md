---
title: "ProjectItem 元素（Visual Studio 项目模板） | Microsoft Docs"
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
  - "<ProjectItem> 元素 [Visual Studio 项目模板]"
  - "ProjectItem 元素 [Visual Studio 项目模板]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem 元素（Visual Studio 项目模板）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定包含在项目模板中的一个文件。  
  
> [!NOTE]
>  `ProjectItem` 元素根据模板是项目的模板还是项的模板，接受不同的特性。  此主题解释项目模板的 `ProjectItem` 元素。  有关项模板的 `ProjectItem` 元素的解释，请参见 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)。  
  
## 语法  
  
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
  
## 特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|`TargetFileName`|可选特性。<br /><br /> 指定从此模板创建项目时项目项的名称和路径。  创建与模板的 .zip 文件中的目录结构不同的目录结构时，或者使用参数替换创建项名称时，此特性非常有用。|  
|`ReplaceParameters`|可选特性。<br /><br /> 一个布尔值，该值指定从此模板创建项目时此项是否具有必须被替换的参数值。  默认值为 `false`。|  
|`OpenInEditor`|可选特性。<br /><br /> 一个布尔值，该值指定从此模板创建项目时此项是否应在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中与其相应的编辑器中打开。<br /><br /> 如果某项的 `OpenInEditor` 的值为 `true`，则忽略该项的 `OpenInWebBrowser` 和 `OpenInHelpBrowser` 特性。<br /><br /> 默认值为 `false`。|  
|`OpenInWebBrowser`|可选特性。<br /><br /> 一个布尔值，该值指定从此模板创建项目时此项是否应在 Web 浏览器中打开。<br /><br /> 只有属于此项目的本地 HTML 文件和文本文件才可以在 Web 浏览器中打开。  不能用此特性打开外部 URL。<br /><br /> 默认值为 `false`。|  
|`OpenInHelpBrowser`|可选特性。<br /><br /> 一个布尔值，该值指定从此模板创建项目时此项是否应在帮助查看器中打开。<br /><br /> 只有属于此项目的本地 HTML 文件和文本文件才可以在帮助浏览器中打开。  不能用此特性打开外部 URL。<br /><br /> 默认值为 `false`。|  
|`OpenOrder`|可选特性。<br /><br /> 指定一个数值，该值表示各项在与其相应的各个编辑器中打开的顺序。  所有值都必须为 10 的倍数。  首次打开具有更高的 `OpenOrder` 值的项。|  
  
### 子元素  
 无。  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[项目](../extensibility/project-element-visual-studio-templates.md)|指定要添加到项目中的文件或目录。|  
  
## 文本值  
 需要一个文本值。  
  
 一个 `string`，它表示模板 .zip 文件中的某个文件的名称或路径。  
  
## 备注  
 `ProjectItem` 是 `Project` 的可选子级。  
  
 可以使用 `TargetFileName` 特性创建与模板 .zip 文件中的目录结构不同的目录结构。  例如，如果 `MyFile.vb` 位于模板 .zip 文件的根级别中，但您希望将此文件放入从此模板创建的所有项目中的名为 `CustomFiles` 的目录里，此时可以使用下面的 XML：  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 对于文件名中包含国际字符的文件，也可以使用 `TargetFileName` 特性来重命名文件。  例如，由于模板 .zip 文件不能包含具有 Unicode 字符的文件名，所以在将文件压缩到 .zip 文件中之前必须对它进行重命名。  `TargetFileName` 特性可以用于将文件名设置回原始 Unicode 文件名。  
  
 还可以使用 `TargetFileName` 特性以及参数重命名文件。  下面的过程说明如何将文件 `MyFile.vb`（存在于模板 .zip 文件的根目录中）重命名为基于项目名称的文件名。  
  
### 使用参数重命名文件  
  
1.  在 .vstemplate 文件中使用以下 XML：  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  在文本编辑器或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中打开此项目文件（对于 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 项目其扩展名为 .vbproj）。  
  
3.  在此项目文件中找到与以下 XML 相似的代码行：  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  用以下 XML 替换此代码行：  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     从此模板创建项目时，将根据用户在**“新建项目”**对话框中输入的名称为文件命名，同时移除所有不安全字符及空格。  有关更多信息，请参见[模板参数](../ide/template-parameters.md)。  
  
## 示例  
 下面的示例演示针对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 应用程序的某个项目模板的元数据。  
  
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
  
## 请参阅  
 [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)   
 [创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)   
 [模板参数](../ide/template-parameters.md)   
 [ProjectItem 元素（Visual Studio 项模板）](../extensibility/projectitem-element-visual-studio-item-templates.md)