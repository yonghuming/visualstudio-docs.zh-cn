---
title: "如何： 创建事件接收器 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 938c03a0bea5a4e96885f1816ddb1c1c13d80ce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-event-receiver"></a>如何：创建事件接收器
  通过创建*事件接收器*，你可以在用户与 SharePoint 项，如列表或列表项交互时响应。 例如，当用户更改日历或从联系人列表中删除名称时，可以触发事件接收器中的代码。 通过本主题后，您可以了解如何将事件接收器添加到列表实例。  
  
 若要完成这些步骤，你必须安装[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和支持的版本的 Windows 和 SharePoint。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。 由于此示例需要 SharePoint 项目，你还必须已完成主题中的过程[演练： 创建网站栏、 内容类型和 SharePoint 列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。  
  
## <a name="adding-an-event-receiver"></a>添加事件接收器  
 在中创建的项目[演练： 为 SharePoint 创建网站栏、 内容类型和列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)包括自定义网站栏、 自定义列表中和内容类型。 在下面的过程中，用户将到演示如何处理 SharePoint 项 （如列表） 中发生事件的列表实例，此项目通过添加一个简单的事件处理程序 （一个事件接收器） 扩展。  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>若要向列表实例中添加事件接收器  
  
1.  打开你在中创建的项目[演练： 创建网站栏、 内容类型和 SharePoint 列表](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)。  
  
2.  在**解决方案资源管理器**，选择 SharePoint 项目节点，名为**Clinic**。  
  
3.  在菜单栏上，选择**项目**，**添加新项**。  
  
4.  下**Visual C#**或**Visual Basic**，展开**SharePoint**节点，然后选择**2010年**项。  
  
5.  在**模板**窗格中，选择**事件接收器**，将其命名为**TestEventReceiver1**，然后选择**确定**按钮。  
  
     **SharePoint 自定义向导**显示。  
  
6.  在**你想进行何种类型的事件接收器？**列表中，选择**列表项事件**。  
  
7.  在**哪个项应为事件源？**列表中，选择**患者 (Clinic\Patients)**。  
  
8.  在**处理以下事件**列表中，选择复选框旁边**项已添加**，然后选择**完成**按钮。  
  
     新的事件接收器的代码文件包含一个名为的单个方法`ItemAdded`。 在下一步的步骤中，你会将代码添加到此方法，以便每个联系人将被命名为 Scott 棕色默认情况下。  
  
9. 将现有`ItemAdded`方法替换为以下代码，，然后选择 F5 键：  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     则代码将运行，并且站点会显示在 web 浏览器中的 SharePoint。  
  
10. 在快速启动栏上，选择**患者**链接，然后再选择**添加新项**链接。  
  
     新项目项的窗体将打开。  
  
11. 在字段中，输入数据，然后选择**保存**按钮。  
  
     选择后**保存**按钮，**患者名称**列将自动更新为 Scott 棕色的名称。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  