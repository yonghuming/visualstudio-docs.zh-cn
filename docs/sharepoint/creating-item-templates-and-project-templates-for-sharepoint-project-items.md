---
title: "创建项模板和项目模板的 SharePoint 项目项 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7ea1c76cda46313458dcac01b415e7541732a26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>为 SharePoint 项目项创建项模板和项目模板
  当定义自定义的 SharePoint 项目项类型时，你可以将其与关联的项模板或项目模板，以便其他开发人员可以使用 Visual Studio 中的项目项。 你还可以创建模板向导。  
  
 例如，Visual Studio 不包括项目模板或项模板以供将字段添加到 SharePoint 站点。 你可以定义 SharePoint 项目项类型表示的字段，然后构造其他开发人员可用于将字段项添加到 SharePoint 项目项模板。 或者，您可以构建项目模板，以便开发人员可以创建新的 SharePoint 项目包含字段项。 在这两种情况下，你还可以提供一个向导，开发人员使用你的模板时，将出现。 此向导可以从开发人员配置项目的新项收集信息。  
  
 项模板和项目模板是包含 Visual Studio 用来创建的项目项或项目的文件的.zip 文件。 有关项模板和项目模板的基础知识的详细信息，请参阅[创建项目和项模板](/visualstudio/ide/creating-project-and-item-templates)。  
  
##  <a name="creatingitemtemplates"></a>创建项模板  
 在创建 SharePoint 项目项的项模板时，有一些始终是必需的文件和可选可能使用的某些类型的项目项的文件。 有关演示如何定义 SharePoint 项目项类型并为它创建项模板的演练，请参阅[演练： 使用项模板，第 1 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
 下表列出了所需的文件，以创建 SharePoint 项目项的项模板。  
  
|所需文件|描述|  
|-------------------|-----------------|  
|.Spdata 文件|这是 XML 文件指定的内容和项目项的默认行为。 此文件必须包含在项模板。 .Spdata 文件的内容的详细信息，请参阅[SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)。|  
|.Vstemplate 文件。|此文件将 Visual Studio 提供显示中的模板所需的信息**添加新项**对话框中，并从模板创建的项目项。 此文件必须包含在项模板。 有关详细信息，请参阅[Visual Studio 模板元数据文件](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|实现的 Visual Studio 扩展程序集<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>接口。|此程序集定义项目项的运行的时的行为。 此程序集必须包含在 VSIX 包带有项模板。 有关详细信息，请参阅[定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)和[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。|  
  
 下表列出了一些可以包含在项模板的最常见的可选文件。 某些类型的项目项可能需要其他文件未在此处列出。  
  
|可选文件|描述|  
|-------------------|-----------------|  
|Elements.xml|A*功能元素*文件。 此文件定义 UI 和创建的项目项的自定义的行为。 每种类型的自定义项，如列表实例、 内容类型或自定义操作，具有不同的架构定义此文件的内容。 有关详细信息，请参阅[构建基块： 功能](http://go.microsoft.com/fwlink/?LinkId=169183)和[功能架构](http://go.microsoft.com/fwlink/?LinkId=169192)。|  
|Schema.xml|列表定义架构文件。 有关详细信息，请参阅[构建基块： 列表和文档库](http://go.microsoft.com/fwlink/?LinkId=177792)和[Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)。|  
|.webpart|A *Web 部件定义*文件。 此文件包含为 Web 部件的属性设置。 有关详细信息，请参阅[构建基块： Web 部件](http://go.microsoft.com/fwlink/?LinkId=177791)。|  
|.ascx|ASP.NET UserControl 文件。 此文件定义可视 Web 部件的 UI。|  
|.aspx|ASP.NET 页文件。 此文件包含定义的应用程序页的 XML 标记。|  
|.cs 或.vb 文件|这些代码文件定义的行为的示例自定义的链接，这些 SharePoint 项具有一个可以从 Visual C# 或 Visual Basic 代码，如应用程序页、 Web 部件和工作流访问的编程模型。|  
  
## <a name="creating-project-templates"></a>创建项目模板  
 在创建 SharePoint 项目模板时，有一些文件始终是可能由某些类型的项目的必需和可选文件。 通常情况下，SharePoint 项目包含至少一个 SharePoint 项目项。 但是，这不是必需的。 例如，你可以定义旨在仅可用于部署 SharePoint 解决方案创建其他项目中的 SharePoint 项目模板。  
  
 有关演示如何定义 SharePoint 项目项类型并为它创建的项目模板的演练，请参阅[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。  
  
 下表列出必须包含在 SharePoint 项目模板的文件。  
  
|所需文件|描述|  
|-------------------|-----------------|  
|.Vstemplate 文件|此文件将 Visual Studio 提供显示中的模板所需的信息**新项目**对话框中和从模板创建项目。 有关详细信息，请参阅[Visual Studio 模板元数据文件](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|Csproj 或.vbproj 文件|这是项目文件。 它定义的内容和配置设置的项目。|  
|Package.package|此文件定义项目的部署包。 当你使用在包设计器为你的项目中自定义解决方案包时，Visual Studio 将此文件中存储有关解决方案包的数据。<br /><br /> 在创建模板的自定义 SharePoint 项目时，我们建议，你只包括所需的最低 Package.package 文件中的内容和使用中的 Api 配置解决方案包<xref:Microsoft.VisualStudio.SharePoint.Packages>命名空间中的扩展与项目模板。 如果这样做，你的项目模板保护以防止将来的更改对 Package.package 文件的结构。 有关演示如何创建具有所需的最小值的 Package.package 文件内容的示例，请参阅[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果你想要直接修改 Package.package 文件，你可以通过在 %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd 使用架构来验证内容。|  
|Package.Template.xml|此文件为 SharePoint 解决方案包 (.wsp) 从项目生成的解决方案清单文件 (manifest.xml) 提供了基础。 如果你想要指定不应更改你的项目类型的用户的某些行为，可以添加到此文件的内容。 有关详细信息，请参阅[构建基块： 解决方案](http://go.microsoft.com/fwlink/?LinkId=169186)和[解决方案架构](http://go.microsoft.com/fwlink/?LinkId=177794)。<br /><br /> 生成解决方案包从项目时，Visual Studio 将包的内容合并和到解决方案的 Package.Template.xml 文件清单文件。 有关生成解决方案包的详细信息，请参阅[如何： 创建 SharePoint 解决方案包 (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
 下表列出可以包含在项目模板的可选文件。  
  
|可选文件|描述|  
|-------------------|-----------------|  
|SharePoint 项目项|你可以包括定义 SharePoint 项目项类型的一个或多个.spdata 文件。 每个.spdata 文件必须具有匹配<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>中 VSIX 包项目模板中包括的扩展程序集的实现。 有关详细信息，请参阅[创建项模板](#creatingitemtemplates)。<br /><br /> 通常情况下，SharePoint 项目包含至少一个 SharePoint 项目项。 但是，这不是必需的。|  
|*featureName*.feature|此文件定义 SharePoint 功能的用于分组以进行部署的多个项目项。 当功能设计器用于在你的项目中自定义功能时，Visual Studio 将此文件中存储有关功能的数据。 如果你想要将项目项分组为不同的功能，则可以包含多个.feature 文件。<br /><br /> 时创建自定义的 SharePoint 项目模板时，我们建议你将仅最小必需的内容包括在每个.feature 文件，并通过使用中的 Api，你将配置功能<xref:Microsoft.VisualStudio.SharePoint.Features>与关联的扩展中的命名空间项目模板。 如果这样做，你的项目模板保护以防止将来的更改对.feature 文件的结构。 有关演示如何创建具有所需的最小值的.feature 文件内容的示例，请参阅[演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果你想要直接修改.feature 文件，你可以通过在 %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd 使用架构来验证内容。|  
|*featureName*。模板.xml|此文件的功能清单文件 (Feature.xml) 中提供的基础，对于每个项目中生成的功能。 如果你想要指定不应更改你的项目类型的用户的某些行为，可以添加到此文件的内容。 有关详细信息，请参阅[构建基块： 功能](http://go.microsoft.com/fwlink/?LinkId=169183)和[Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795)文件。<br /><br /> Visual Studio 生成项目从解决方案包时，将每个对的内容合并*featureName*.feature 文件和*featureName*。转换为特征的模板.xml 文件清单文件。 有关生成解决方案包的详细信息，请参阅[如何： 创建 SharePoint 解决方案包 (wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
## <a name="creating-wizards-for-item-templates-and-project-templates"></a>为项模板和项目模板创建向导  
 在定义 SharePoint 项目项类型并将其与项目或项模板相关联后，你还可以创建向导。 向导将显示当开发人员使用项模板将 SharePoint 项目项添加到项目中，或当开发人员使用项目模板创建一个包含 SharePoint 项目项的新项目。 可以使用该向导，以从开发人员收集信息并初始化新的 SharePoint 项目项。  
  
 有关演示如何创建项模板和项目模板中的向导的演练，请参阅[演练： 使用项模板，第 2 部分创建自定义操作项目项](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)和[演练： 创建站点栏项目项的项目模板，第 2 部分](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## <a name="see-also"></a>另请参阅  
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [演练： 使用项模板创建的自定义操作项目项，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [演练： 使用项模板创建的自定义操作项目项，第 2 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [演练： 使用项目模板，第 2 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [创建项目和项模板](/visualstudio/ide/creating-project-and-item-templates)  
  
  