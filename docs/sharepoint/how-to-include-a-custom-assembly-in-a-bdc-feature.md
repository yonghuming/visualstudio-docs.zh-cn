---
title: "如何： 在 BDC 功能中包含自定义程序集 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5916da8b7aa5018824ffe8040e7184fe6d1bf31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>如何：在 BDC 功能中引入自定义程序集
  你的项目可以与同一解决方案中其他项目中引用程序集。 但是，你必须将添加这些程序集到项目的功能文件通过**分配引用程序集 Lobsystem 到**对话框。  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>要包含在业务数据连接 (BDC) 功能中的自定义程序集  
  
1.  在**解决方案资源管理器**，选择包含 BDC 模型的文件夹。  
  
2.  在 **“视图”** 菜单上，单击 **“属性窗口”**。  
  
3.  在**属性**窗口中，选择**程序集**属性，然后单击省略号按钮 (![ASP.NET 移动设计器椭圆](../sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器椭圆"))。  
  
     **分配引用程序集 Lobsystem 到**对话框随即出现。  
  
4.  在**选择的程序集**列表中，选择自定义程序集。  
  
    > [!NOTE]  
    >  程序集只能出现在**分配引用程序集 Lobsystem 到**对话框中，如果你已添加到包含的程序集的项目的引用。 有关详细信息，请参阅[如何： 添加或删除引用通过使用添加引用对话框](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
5.  在**引用属性**组中，打开列表为显示**LobSystem 范围**属性，选择的方法，使用自定义程序集，然后选择 LOB 系统**确定**按钮。  
  
    > [!NOTE]  
    >  若要调试自定义程序集中的代码，必须将程序集添加到解决方案包中。 有关详细信息，请参阅[如何： 添加和移除附加程序集](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 使用资源文件来指定本地化的名称、 属性和权限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 向 SharePoint 项目中添加现有 BDC 模型文件](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 创建 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [将业务数据集成到 SharePoint 中](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  