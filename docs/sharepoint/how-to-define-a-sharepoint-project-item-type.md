---
title: "如何： 定义 SharePoint 项目项类型 |Microsoft 文档"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c5f39fea52b6f417b046a7ff1f72dff1190a038
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>如何：定义 SharePoint 项目项类型
  当你想要创建自定义 SharePoint 项目项时，请定义项目项类型。 有关详细信息，请参阅[定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)。  
  
### <a name="to-define-a-project-item-type"></a>若要定义项目项类型  
  
1.  创建类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 接口的类。  
  
4.  将以下属性添加到类：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 此属性使 Visual Studio 发现和加载你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>实现。 传递<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>给特性构造函数的类型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 在项目项类型定义中，此属性指定新的报表项的字符串标识符。 我们建议你使用格式*公司名称*。*功能名称*以帮助确保所有项目项都具有一个唯一的名称。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>。 此属性指定要为此项目项中显示的图标**解决方案资源管理器**。 此属性是可选的;如果不将其应用到你的类，Visual Studio 将显示您的项目项的默认图标。 如果设置此属性时，将传递图标或位图嵌入到程序集的完全限定的名称。  
  
5.  实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法，使用成员*projectItemTypeDefinition*参数定义的项目项类型的行为。 此参数是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>提供对中定义的事件的访问的对象<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>接口。 若要访问你的项目项类型的特定实例，处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>如事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何定义一个简单的项目项类型。 此项目项类型将消息写入**输出**窗口和**错误列表**窗口，当用户将此类型的项目项添加到项目。  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 此示例使用 SharePoint 项目服务要写入到消息**输出**窗口和**错误列表**窗口。 有关详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>部署项目项  
 若要启用其他开发人员能够使用您的项目项，创建项目模板或项目项模板。 有关详细信息，请参阅[创建项模板和 SharePoint 项目项的项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 若要部署的项目项，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集，该模板后和你想要随此项目项分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [定义自定义 SharePoint 项目项类型](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [为 SharePoint 项目项创建项模板和项目模板](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [演练： 使用项模板创建的自定义操作项目项，第 1 部分](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [演练： 使用项目模板，第 1 部分中创建网站栏项目项](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [如何： 向自定义 SharePoint 项目项类型添加属性](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [如何：将快捷菜单项添加到自定义 SharePoint 项目项类型](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  