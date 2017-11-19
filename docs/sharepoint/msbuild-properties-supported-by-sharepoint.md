---
title: "支持的 SharePoint 的 MSBuild 属性 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, MSBuild properties
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53e90448d5e7a24f4904f9c4ea02ac041531ce02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint 支持的 MSBuild 属性
  任何[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]Microsoft.VisualStudio.SharePoint.targets 文件、 项目文件中或项目用户文件中定义的属性可在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 项目。 除了常见[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]项目，SharePoint 提供的属性定义了特定于 SharePoint 项目的其他属性。  
  
 有关常见的列表[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]属性，请参阅[常用 MSBuild 项目属性](http://go.microsoft.com/fwlink/?LinkID=168687)。 对于您的编程语言支持的属性的完整列表，请查看.targets 文件、 项目文件 （.csproj 或.vbproj） 或项目用户文件 (csproj.user 或。 vbproj.user)。  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>MSBuild 属性特定于 SharePoint  
 下表列出[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]尤其适用于 SharePoint 项目中的属性[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 其他属性也存在，但它们以供内部使用。  
  
|属性名|描述|  
|-------------------|-----------------|  
|SharePointSiteUrl|一个字符串，表示[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]到 SharePoint 站点。|  
|SandboxedSolution|一个布尔值，该值指示解决方案是否为沙盒解决方案。|  
|ActiveDeploymentConfiguration|活动部署配置。|  
|IncludeAssemblyInPackage|一个布尔值，该值指示程序集包含包文件中。|  
|PreDeploymentCommand|一个字符串值，表示要在预先部署命令步骤中执行的命令。|  
|PostDeploymentCommand|一个字符串值，表示要在部署后命令步骤中执行的命令。|  
|CustomBeforeSharePointTargets|一个字符串，表示的路径[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]目标文件。 如果目标文件存在，并定义，它是之前导入任何 SharePoint 目标数据。 此属性允许你自包过程定义的预定义与包装相关的属性，而无需修改随附的 SharePoint 目标文件，但目标文件仍适用于所有 SharePoint 项目。|  
|CustomAfterSharePointTargets|一个字符串，表示的路径[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]目标文件。 如果目标文件存在，并且定义，会导入所有的 SharePoint 目标数据。 此属性，可以通过重写了与包装相关的属性和目标，而无需修改随附的 SharePoint 目标文件，自定义包进程，但目标文件仍适用于所有 SharePoint 项目。|  
|LayoutPath|一个字符串，表示每个文件打包的临时存放之前添加到.wsp 文件的根目录。 此路径可以是有助于你了解当重写 BeforeLayout 和 AfterLayout 目标，以添加、 删除或修改要打包的文件，因为你可以使用它来更改此.wsp 文件的内容。|  
|BasePackagePath|一个字符串，表示在其中放置包的文件夹。 此值使用项目中，如 Bin\Debug 的输出目录。|  
|PackageExtension|表示要追加到包的文件扩展名的字符串。 默认值为 wsp。|  
|AssemblyDeploymentTarget|一个字符串，表示项目程序集在 SharePoint 服务器的部署位置的位置。 其值为 GlobalAssemblyCache （默认） 或 web 应用程序。 此外可以在属性窗口中设置此属性。|  
|PackageWithValidation|一个布尔值，指定是否进行打包之前执行验证。 此属性允许您在生成包时忽略验证错误。|  
|ValidatePackageDependsOn|一个字符串，定义要在 ValidatePackage 目标之前执行的其他目标。|  
|TokenReplacementFileExensions|一个字符串，定义具有在打包过程中替换其令牌的文件。|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>在属性页中使用 MSBuild 属性  
 为了地提高灵活性，而不是使用内的硬编码字符串**预先部署命令行**和**后期部署命令行**框在 SharePoint 属性页上，你可以使用 SharePoint作为自变量的属性。 例如，而不是指定特定[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]字符串为 SharePoint 站点，则可以使用`$(SharePointSiteUrl)`。  
  
> [!NOTE]  
>  你可以使用[!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]变量语法`$(` *propertyName* `)`或环境变量语法`%` *propertyName* `%`可以指定的属性。  
  
## <a name="see-also"></a>另请参阅  
 [MSBuild 参考](/visualstudio/msbuild/msbuild-reference)  
  
  