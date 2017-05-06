---
title: "SharePoint 支持的 MSBuild 属性"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, MSBuild 属性"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# SharePoint 支持的 MSBuild 属性
  Microsoft.VisualStudio.SharePoint.targets 文件、项目文件或项目用户文件中定义的任何 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 属性都可在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 项目中使用。  除了项目提供的通用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 属性外，SharePoint 还定义一些特定于 SharePoint 项目的其他属性。  
  
 有关通用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 属性的列表，请参见 [Common MSBuild 项目属性](http://go.microsoft.com/fwlink/?LinkID=168687)。  有关您的编程语言支持的属性的完整列表，请查看 .targets 文件、项目文件（.csproj 或 .vbproj）或项目用户文件（csproj.user 或 .vbproj.user）。  
  
## 特定于 SharePoint 的 MSBuild 属性  
 下表列出了特定适用于 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint 项目的 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 属性。  其他属性也存在，但它们供内部使用。  
  
|属性名|说明|  
|---------|--------|  
|SharePointSiteUrl|一个表示 SharePoint 网站 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 的字符串。|  
|SandboxedSolution|一个布尔值，该值指示解决方案是否为沙盒解决方案。|  
|ActiveDeploymentConfiguration|活动部署配置。|  
|IncludeAssemblyInPackage|一个布尔值，该值指示包文件中是否包括程序集。|  
|PreDeploymentCommand|一个字符串值，该值表示要在预先部署命令步骤中执行的命令。|  
|PostDeploymentCommand|一个字符串值，该值表示要在后期部署命令步骤中执行的命令。|  
|CustomBeforeSharePointTargets|一个表示 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 目标文件路径的字符串。  如果目标文件存在且已定义，则该文件将在任何 SharePoint 目标数据之前导入。  此属性使您无需修改附带的 SharePoint 目标文件即可通过预定义与打包相关的属性来自定义包过程，而目标文件仍然适用于所有 SharePoint 项目。|  
|CustomAfterSharePointTargets|一个表示 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 目标文件路径的字符串。  如果目标文件存在且已定义，则该文件将在所有 SharePoint 目标数据之后导入。  此属性使您不必修改附带的 SharePoint 目标文件即可通过重写与打包相关的属性和目标来自定义包过程，而目标文件仍然适用于所有 SharePoint 项目。|  
|LayoutPath|一个表示根目录的字符串，在将每个要打包的文件添加到 .wsp 文件之前，会将这些文件暂时放在该目录中。  若要了解何时重写 BeforeLayout 和 AfterLayout 目标以便添加、移除或修改要打包的文件，此路径可能非常有用，因为您可以使用它来更改 .wsp 文件的内容。|  
|BasePackagePath|一个字符串，表示在其中放置包的文件夹。  此值使用项目的输出目录，例如 Bin\\Debug。|  
|PackageExtension|一个字符串，表示要追加到包的文件扩展名。  默认值为 wsp。|  
|AssemblyDeploymentTarget|一个字符串，表示在 SharePoint 服务器上部署项目程序集的位置。  其值为 GlobalAssemblyCache（默认值）或 WebApplication。  也可以在“属性”窗口中设置此属性。|  
|PackageWithValidation|一个布尔值，该值指定是否在打包之前执行验证。  此属性使您可以在生成包时忽略验证错误。|  
|ValidatePackageDependsOn|一个字符串，定义要在 ValidatePackage 目标之前执行的其他目标。|  
|TokenReplacementFileExensions|一个字符串，定义其标记在打包过程被替换的文件。|  
  
## 在属性页中使用 MSBuild 属性  
 为了灵活起见，您可以使用 SharePoint 属性作为参数，而不是在 SharePoint 属性页上的**“预先部署命令行”**和**“后期部署命令行”**框中使用硬编码的字符串。  例如，您可以使用 `$(SharePointSiteUrl)`，而不是指定 SharePoint 网站的具体 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 字符串。  
  
> [!NOTE]  
>  可以使用 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 变量语法 `$(`*propertyName*`)` 或环境变量语法 `%`*propertyName*`%` 来指定属性。  
  
## 请参阅  
 [MSBuild 参考](../msbuild/msbuild-reference.md)  
  
  