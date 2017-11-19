---
title: "扩展 SharePoint 项目系统中保存数据 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3605558fd1fd9263c5dad7ec7bc295b7f095a185
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>在 SharePoint 项目系统的扩展中保存数据
  扩展 SharePoint 项目系统时，你可以保存仍然存在后关闭 SharePoint 项目的字符串数据。 数据是与特定项目项或与项目本身通常相关联。  
  
 如果你有不需要保留的数据，可以将数据添加到实现 SharePoint 工具对象模型中的任何对象<xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>接口。 有关详细信息，请参阅[关联与 SharePoint 工具扩展的自定义数据](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)。  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>将数据保存关联项目项  
 当必须与特定的 SharePoint 项目项，如你将添加到项目项属性的值相关联的数据时你可以将数据保存到项目项的.spdata 文件。 若要执行此操作，使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>属性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>对象。 你将添加到此属性的数据保存在**ExtensionData**项目项的.spdata 文件中的元素。 有关详细信息，请参阅[ExtensionData 元素](../sharepoint/extensiondata-element.md)。  
  
 下面的代码示例演示如何使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>属性将保存在自定义的 SharePoint 项目项类型中定义的字符串属性的值。 若要查看此示例中的上下文中的一个更大的示例，请参阅[如何： 向自定义 SharePoint 项目项类型添加属性](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)。  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>将数据保存关联项目  
 如果具有项目级别的数据，如 SharePoint 项目中添加的属性值可以将数据保存到项目文件 （.csproj 文件或.vbproj 文件） 或项目用户选项文件 (。 csproj.user 文件或。 vbproj.user 文件)。 您选择将保存中的数据的文件取决于你想要使用的数据的方式：  
  
-   如果你想要向所有开发人员打开 SharePoint 项目提供的数据，则将数据保存到项目文件。 此文件是始终签入到源代码管理数据库，因此此文件中的数据可供其他开发人员签出该项目。  
  
-   如果你想要仅供的当前开发人员已在 Visual Studio 中打开 SharePoint 项目的数据，则将数据保存到项目的用户选项文件。 此文件是不通常签入到源代码管理数据库，因此此文件中的数据不可用的其他开发人员签出该项目。  
  
### <a name="saving-data-to-the-project-file"></a>将数据保存到项目文件  
 若要将数据保存到项目文件，将转换<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>对象传递给<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>对象，，然后使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>方法。 下面的代码示例演示如何使用此方法将项目属性的值保存到项目文件。 若要查看此示例中的上下文中的更大的示例，请参阅[如何： 向 SharePoint 项目中添加属性](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 有关将转换的详细信息<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>Visual Studio 自动化对象模型或集成对象模型中其他类型的对象请参阅[转换之间 SharePoint 项目系统类型和其他 Visual Studio 项目类型](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>将数据保存到项目的用户选项文件  
 若要将数据保存到项目的用户选项文件，使用<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>属性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>对象。 下面的代码示例演示如何使用此属性将项目属性的值保存到项目用户选项文件。 若要查看此示例中的上下文中的更大的示例，请参阅[如何： 向 SharePoint 项目中添加属性](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)。  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 项目系统](../sharepoint/extending-the-sharepoint-project-system.md)   
 [将自定义数据与 SharePoint 工具扩展相关联](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [在 SharePoint 项目系统类型和其他 Visual Studio 项目类型之间进行转换](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  