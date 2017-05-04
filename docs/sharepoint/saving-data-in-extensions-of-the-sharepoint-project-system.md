---
title: "Saving Data in Extensions of the SharePoint Project System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  在扩展 SharePoint 项目系统时，可以保存在关闭 SharePoint 项目后继续存在的字符串数据。  该数据通常与特定项目项或项目本身关联。  
  
 如果您的数据无需保留，则可将该数据添加到实现 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> 接口的 SharePoint 工具对象模型中的任何对象。  有关更多信息，请参见[Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## 保存与项目项关联的数据  
 当您的数据与特定 SharePoint 项目项关联（例如，添加到项目项的属性的值）时，可以将数据保存到此项目项的 .spdata 文件。  为此，请使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 对象的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 属性。  添加到此属性的数据将保存在项目项的 .spdata 文件中的 **ExtensionData** 元素中。  有关更多信息，请参见 [ExtensionData Element](../sharepoint/extensiondata-element.md)。  
  
 下面的代码示例演示如何使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 属性保存在自定义 SharePoint 项目项类型中定义的字符串属性的值。  若要在一个更大的示例上下文中查看此示例，请参见[How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## 保存与项目关联的数据  
 当您具有项目级数据（例如，添加到 SharePoint 项目的属性的值）时，可以将该数据保存到项目文件（.csproj 文件或 .vbproj 文件）或项目用户选项文件（.csproj.user 文件或 .vbproj.user 文件）。  选择用来保存数据的文件取决于您希望使用该数据的方式：  
  
-   如果您希望该数据对所有打开 SharePoint 项目的开发人员可用，请将该数据保存到项目文件。  由于总是会将此文件签入源代码管理数据库，因此此文件中的数据对签出该项目的其他开发人员可用。  
  
-   如果您希望数据仅对已在 Visual Studio 中打开 SharePoint 项目的当前开发人员可用，则将数据保存到项目用户选项文件中。  由于通常不会将此文件签入源代码管理数据库，因此此文件中的数据对签出该项目的其他开发人员不可用。  
  
### 将数据保存到项目文件中  
 若要将数据保存到项目文件中，请将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 对象转换为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 对象，然后使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 方法。  下面的代码示例演示如何使用此方法将项目属性的值保存到项目文件中。  若要在一个更大的示例上下文中查看此示例，请参见[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 有关将 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 对象转换为 Visual Studio 自动化对象模型或集成对象模型中的其他类型的更多信息，请参见[Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
### 将数据保存到项目用户选项文件中  
 若要将数据保存到项目用户选项文件中，请使用 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 对象的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 属性。  下面的代码示例演示如何使用此属性将项目属性的值保存到项目用户选项文件中。  若要在一个更大的示例上下文中查看此示例，请参见[How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## 请参阅  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  