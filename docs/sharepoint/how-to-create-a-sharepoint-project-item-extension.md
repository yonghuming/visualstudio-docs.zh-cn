---
title: "如何： 创建 SharePoint 项目项扩展 |Microsoft 文档"
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e9faaf0b38623347c2b6e8ff7351f625416e82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>如何：创建 SharePoint 项目项扩展
  当你想要将功能添加到已安装在 Visual Studio 中的 SharePoint 项目项创建项目项扩展。 有关详细信息，请参阅[扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)。  
  
### <a name="to-create-a-project-item-extension"></a>若要创建项目项扩展  
  
1.  创建类库项目。  
  
2.  添加对下列程序集的引用：  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  创建实现 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 接口的类。  
  
4.  将以下属性添加到类：  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>。 此属性使 Visual Studio 发现和加载你<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>实现。 传递<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>给特性构造函数的类型。  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 在项目项扩展中，此属性标识你想要扩展的项目项。 将项目项的 ID 传递给特性构造函数。 Visual Studio 附带的项目项的 Id 的列表，请参阅[扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)。  
  
5.  实现中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>方法，使用成员*projectItemType*参数定义你的扩展的行为。 此参数是<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>提供对中定义的事件的访问的对象<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>接口。 若要访问所扩展的项目项类型的特定实例，处理<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>如事件<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>和<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>。  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何创建一个简单的事件接收器项目项扩展。 每次用户将事件接收器项目项添加到 SharePoint 项目，此扩展将消息写入**输出**窗口和**错误列表**窗口。  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 此示例使用 SharePoint 项目服务要写入到消息**输出**窗口和**错误列表**窗口。 有关详细信息，请参阅[使用 SharePoint 项目服务](../sharepoint/using-the-sharepoint-project-service.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要引用以下程序集：  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>部署扩展  
 若要部署的扩展，创建[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]扩展 (VSIX) 包的程序集和你想要随此扩展分发的任何其他文件。 有关详细信息，请参阅[部署 Visual Studio 中的 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [扩展 SharePoint 项目项](../sharepoint/extending-sharepoint-project-items.md)   
 [演练：扩展 SharePoint 项目项类型](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  