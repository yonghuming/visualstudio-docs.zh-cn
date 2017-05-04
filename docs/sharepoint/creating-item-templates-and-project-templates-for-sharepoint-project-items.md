---
title: "Creating Item Templates and Project Templates for SharePoint Project Items | Microsoft Docs"
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
helpviewer_keywords: 
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  在定义自定义 SharePoint 项目项类型时，可以将其与项模板或项目模板关联，以便其他开发人员可在 Visual Studio 中使用该项目项。  也可以为模板创建向导。  
  
 例如， Visual Studio 不包括用于向 SharePoint 网站中添加字段的项目模板或项模板。  您可以定义表示字段的 SharePoint 项目项类型，然后构造其他开发人员可用于向 SharePoint 项目中添加字段项的项模板。  或者，您可以构造项目模板，以便开发人员能创建包含字段项的新 SharePoint 项目。在这两种情况下，您还可以提供显示的向导当开发人员使用模板。  此向导可从开发人员处收集信息以配置新项或项目。  
  
 项模板和项目模板都是 .zip 文件，其中包含 Visual Studio 用于创建项目项或项目的文件。  有关项模板和项目模板的基本元素的更多信息，请参见 [在 Visual Studio 中创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)。  
  
##  <a name="creatingitemtemplates"></a> 创建项模板  
 在为 SharePoint 项目项创建项模板时，有一些始终需要的文件和一些可由某些类型的项目项使用的可选文件。  有关演示如何定义 SharePoint 项目项类型并为其创建项模板的演练，请参见[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)。  
  
 下表列出了为 SharePoint 项目项创建项模板的必需文件。  
  
|必需文件|描述|  
|----------|--------|  
|一个 .spdata 文件|此文件是一个指定项目项的内容和默认行为的 XML 文件。  此文件必须包含在项模板中。  有关 .spdata 文件的内容的更多信息，请参见 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)。|  
|一个 .vstemplate 文件。|此文件为 Visual Studio 提供了在**“添加新项”**对话框中显示模板和从模板创建项目项所需的信息。  此文件必须包含在项模板中。  有关更多信息，请参见[NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/zh-cn/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|一个实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口的 Visual Studio 扩展程序集。|此程序集定义了项目项的运行时行为。  此程序集必须与项模板一起包含在 VSIX 包中。  有关更多信息，请参见[Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)和[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。|  
  
 下表列出了可包含在项模板中的一些最常见的可选文件。  某些类型的项目项可能需要未在此处列出的其他文件。  
  
|可选文件|描述|  
|----------|--------|  
|Elements.xml|一个功能元素文件。  此文件定义项目项创建的自定义项的 UI 和行为。  每种类型的自定义项（例如列表实例、内容类型或自定义操作）都有不同的架构，该架构定义此文件的内容。  有关更多信息，请参见 [Building Block: Features](http://go.microsoft.com/fwlink/?LinkId=169183)（生成块：功能）和 [Feature Schemas](http://go.microsoft.com/fwlink/?LinkId=169192)（功能架构）。|  
|Schema.xml|列表定义的架构文件。  有关更多信息，请参见 [Building Block: Lists and Document Libraries](http://go.microsoft.com/fwlink/?LinkId=177792)（生成块：列表和文档库）和 [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793)。|  
|.webpart|一个 Web 部件定义文件。  此文件包含 Web 部件的属性设置。  有关更多信息，请参见 [Building Block: Web Parts](http://go.microsoft.com/fwlink/?LinkId=177791)（生成块：Web 部件）。|  
|.ascx|一个 ASP.NET UserControl 文件。  此文件定义可视 Web 部件的 UI。|  
|.aspx|一个 ASP.NET 页面文件。  此文件包含定义应用程序页的 XML 标记。|  
|.cs 或 .vb 文件|这些代码文件定义具有可从 Visual C\# 或 Visual Basic 代码中访问的编程模型（例如应用程序页、Web 部件和工作流）的 SharePoint 自定义项的行为。|  
  
## 创建项目模板  
 在创建 SharePoint 项目模板时，有一些始终需要的文件和一些可由某些类型的项目使用的可选文件。  通常，SharePoint 项目至少包含一个 SharePoint 项目项。  但这不是必需的。  例如，您可以定义一个 SharePoint 项目模板，该项目模板只应用于部署在其他项目中创建的 SharePoint 解决方案。  
  
 有关演示如何定义 SharePoint 项目项类型并为其创建项目模板的演练，请参见[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。  
  
 下表列出了必须包含在 SharePoint 项目模板中的文件。  
  
|必需文件|描述|  
|----------|--------|  
|一个 .vstemplate 文件。|此文件为 Visual Studio 提供了在**“新建项目”**对话框中显示模板和从模板创建项目所需的信息。  有关更多信息，请参见[NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/zh-cn/129d59b5-7f9c-4daf-9832-eaedb3c4c961)。|  
|一个 csproj 文件或 .vbproj 文件|此文件是项目文件。  它定义了项目的内容和配置设置。|  
|Package.package|此文件定义项目的部署包。  当您使用包设计器来自定义项目的解决方案包时，Visual Studio 会将有关该解决方案包的数据存储在此文件中。<br /><br /> 在创建自定义 SharePoint 项目模板时，我们建议您仅在 Package.package 文件中包括最少量的必需内容，并建议您使用与项目模板关联的扩展中的 <xref:Microsoft.VisualStudio.SharePoint.Packages> 命名空间中的 API 来配置解决方案包。  如果这样做，项目模板将得到保护，不会受到以后更改 Package.package 文件的结构的影响。  有关演示如何创建仅包含最少量必需内容的 Package.package 文件的示例，请参见[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果要直接修改 Package.package 文件，您可以通过使用位于 %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd 的架构来验证内容。|  
|Package.Template.xml|此文件为从项目生成的 SharePoint 解决方案包 \(.wsp\) 的解决方案清单文件 \(manifest.xml\) 提供了基础。  如果要指定不应由项目类型的用户更改的某种行为，则可以向此文件中添加内容。  有关更多信息，请参见 [Building Block: Solutions](http://go.microsoft.com/fwlink/?LinkId=169186)（生成块：解决方案）和 [Solution Schema](http://go.microsoft.com/fwlink/?LinkId=177794)（解决方案架构）。<br /><br /> 当您从项目生成解决方案包时，Visual Studio 会将 Package.package 和 Package.Template.xml 文件的内容合并为解决方案清单文件。  有关生成解决方案包的更多信息，请参见[How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/zh-cn/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
 下表列出了可包含在项目模板中的可选文件。  
  
|可选文件|描述|  
|----------|--------|  
|SharePoint 项目项|可以包含一个或多个定义 SharePoint 项目项类型的 .spdata 文件。  对于每个 .spdata 文件，在与项目模板一起包含在 VSIX 包中的扩展程序集中必须有一个与之匹配的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 实现。  有关更多信息，请参见[创建项模板](#creatingitemtemplates)。<br /><br /> 通常，SharePoint 项目至少包含一个 SharePoint 项目项。  但这不是必需的。|  
|*功能名称*.feature|此文件定义用于为部署将若干项目项分组的 SharePoint 功能。  当您使用功能设计器在项目中自定义功能时，Visual Studio 会将有关功能的数据存储在此文件中。  如果要将项目项分组为不同的功能，您可以包括多个 .feature 文件。<br /><br /> 在创建自定义 SharePoint 项目模板时，我们建议您仅在每个 feature 文件中包括最少量的必需内容，并建议您使用与项目模板关联的扩展中的 <xref:Microsoft.VisualStudio.SharePoint.Features> 命名空间中的 API 来配置功能。  如果这样做，项目模板将得到保护，不会受到以后更改 .feature 文件的结构的影响。  有关演示如何创建仅包含最少量必需内容的 .feature 文件的示例，请参见[演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)。<br /><br /> 如果要直接修改 .feature 文件，您可以通过使用位于 %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd 的架构来验证内容。|  
|*功能名称*.Template.xml|此文件为从项目生成的每个功能的功能清单文件 \(Feature.xml\) 提供了基础。  如果要指定不应由项目类型的用户更改的某种行为，则可以向此文件中添加内容。  有关更多信息，请参见 [Building Block: Features](http://go.microsoft.com/fwlink/?LinkId=169183)（生成块：功能）和 [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) 文件。<br /><br /> 当您从项目生成解决方案包时，Visual Studio 会将每对 *功能名称*.feature 文件和 *功能名称*.Template.xml 文件的内容合并为一个功能清单文件。  有关生成解决方案包的更多信息，请参见[How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/zh-cn/b24be45c-e91d-49bb-afb0-7b265404214b)。|  
  
## 为项模板和项目模板创建向导  
 在定义 SharePoint 项目项类型并将其与项模板或项目模板关联后，也可以创建向导。  当开发人员使用项模板向项目中添加 SharePoint 项目项时，或当开发人员使用项目模板创建包含 SharePoint 项目项的新项目时，该向导将显示。  该向导既可用于从开发人员处收集信息，又可用于初始化新的 SharePoint 项目项。  
  
 有关演示如何为项模板和项目模板创建向导的演练，请参见[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)和[演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)。  
  
## 请参阅  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [演练：使用项目模板创建网站栏项目项（第 1 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [演练：使用项目模板创建网站栏项目项（第 2 部分）](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [在 Visual Studio 中创建自定义项目和项模板](../ide/creating-project-and-item-templates.md)  
  
  