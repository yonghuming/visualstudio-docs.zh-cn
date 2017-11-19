---
title: "如何： 创建事件接收器的特定列表实例 |Microsoft 文档"
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
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3db5af044b1e3eb25e68c96a42335082fd3523f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>如何：为特定列表实例创建事件接收器
  对列表定义的任何实例中发生的事件的响应列表实例事件接收器。 虽然事件接收器模板不会启用的特定列表实例的目标，你可以修改事件接收器划归到以响应特定列表实例中的事件的列表定义。  
  
 若要面向特定列表实例，然后在事件接收器，Elements.xml 将`ListTemplateId`与`ListUrl`并添加列表实例的 URL。  
  
## <a name="creating-a-list-instance-event-receiver"></a>创建列表实例事件接收器  
 以下步骤显示如何修改列表项事件接收器仅响应自定义公告列表实例中发生的事件。  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>若要修改事件接收器响应的特定列表实例  
  
1.  在浏览器中打开 SharePoint 网站。  
  
2.  在导航窗格中，**列出**链接。  
  
3.  在**所有站点内容**页上，选择**创建**链接。  
  
4.  在**创建**对话框框中，选择**公告**类型，请将公告**命名为 TestAnnouncements**，然后选择**创建**按钮。  
  
5.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，创建一个事件接收器项目。  
  
6.  在**你想进行何种类型的事件接收器？**列表中，选择**列表项事件**。  
  
    > [!NOTE]  
    >  你还可以选择任何其他类型的作用域以列表定义等的事件接收器**列出的电子邮件事件**或**列表工作流事件**。  
  
7.  在**哪个项应为事件源？**列表中，选择**公告**。  
  
8.  在**处理以下事件**列表中，选择**某一项添加**复选框，然后依次**完成**按钮。  
  
9. 在**解决方案资源管理器**，EventReceiver1，下打开 Elements.xml。  
  
     事件接收器当前使用以下行来引用公告列表定义：  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     将此行更改为以下文本：  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     将仅响应发生在新的事件在事件接收器**命名为 TestAnnouncements**刚创建的公告列表。 你可以更改`ListURL`特性来引用 SharePoint 服务器上的任何列表实例。  
  
10. 为事件接收器中打开代码文件和 ItemAdding 方法中放置一个断点。  
  
11. 选择 F5 生成并运行解决方案。  
  
12. 在 SharePoint 中，选择**命名为 TestAnnouncements**在导航窗格中的链接。  
  
13. 选择**添加新公告**链接。  
  
14. 有关该公告，输入标题，然后选择**保存**按钮。  
  
     请注意到自定义公告列表添加新项时，命中断点。  
  
15. 选择 F5 继续。  
  
16. 在导航窗格中，选择**列出**链接，然后再选择**公告**链接。  
  
17. 添加新公告。  
  
     请注意，新公告上不会触发事件接收器，因为接收方被配置为仅对在自定义公告列表实例中，事件做出响应**命名为 TestAnnouncements**。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  