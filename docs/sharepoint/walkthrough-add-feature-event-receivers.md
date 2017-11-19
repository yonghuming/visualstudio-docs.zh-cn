---
title: "演练： 添加功能事件接收器 |Microsoft 文档"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27d565a51c026a6e143e18f122039d90627f55ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-add-feature-event-receivers"></a>演练：添加功能事件接收器
  功能事件接收器是在 SharePoint 中的以下功能相关的事件之一发生时执行的方法：  
  
-   功能的安装。  
  
-   功能激活。  
  
-   一项功能将停用。  
  
-   删除功能时。  
  
 本演练演示如何将事件接收器添加到 SharePoint 项目中的功能。 它演示了下列任务：  
  
-   使用功能事件接收器创建一个空的项目。  
  
-   处理**FeatureDeactivating**方法。  
  
-   使用 SharePoint 项目对象模型向公告列表添加公告。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>先决条件  
 你需要以下组件来完成本演练：  
  
-   支持的 Microsoft Windows 和 SharePoint 版本。 有关详细信息，请参阅[有关开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
## <a name="creating-a-feature-event-receiver-project"></a>创建功能事件接收器项目  
 首先，创建一个项目以包含功能事件接收器。  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>若要使用功能事件接收器创建项目  
  
1.  在菜单栏上，选择**文件**，**新建**，**项目**以显示**新项目**对话框。  
  
2.  展开**SharePoint**下**Visual C#**或**Visual Basic**，然后选择**2010年**节点。  
  
3.  在**模板**窗格中，选择**SharePoint 2010 项目**模板。  
  
     您为功能事件接收器使用此项目类型，因为它们具有没有项目模板。  
  
4.  在**名称**框中，输入**FeatureEvtTest**，然后选择**确定**按钮以显示**SharePoint 自定义向导**。  
  
5.  上**指定用于调试的站点和安全性级别**页上，输入你想要添加新的自定义字段项，SharePoint 服务器站点的 URL 或使用默认位置 (http://\<*系统名称*> /)。  
  
6.  在**此 SharePoint 解决方案的信任级别是什么？**部分中，选择**部署为场解决方案**选项按钮。  
  
     有关沙盒解决方案与场解决方案的详细信息，请参阅[沙盒解决方案注意事项](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  选择**完成**按钮，然后请注意，一种功能，名为 Feature1 出现下**功能**节点。  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>向功能添加事件接收器  
 接下来，添加功能事件接收器，并添加在停用该功能时执行的代码。  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>若要添加到功能事件接收器  
  
1.  打开功能节点的快捷菜单，然后选择**添加功能**创建一项功能。  
  
2.  下**功能**节点，打开快捷菜单**Feature1**，然后选择**添加事件接收器**将添加到功能事件接收器。  
  
     这将添加 Feature1 下的代码文件。 在这种情况下，它名为 Feature1.EventReceiver.cs 或 Feature1.EventReceiver.vb，具体取决于你的项目的开发语言。  
  
3.  如果你的项目用编写[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]，如果它尚不存在的事件接收器顶部添加以下代码：  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  事件接收器类中包含几个注释掉的方法，后者将作为事件。 替换**FeatureDeactivating**方法替换为以下：  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>测试功能事件接收器  
 接下来，停用要测试的功能是否**FeatureDeactivating**方法输出到 SharePoint 公告列表的公告。  
  
#### <a name="to-test-the-feature-event-receiver"></a>若要测试功能事件接收器  
  
1.  将项目的值设置**活动部署配置**属性**无激活**。  
  
     设置此属性可防止功能在 SharePoint 中激活，并使你能够调试功能事件接收器。 有关详细信息，请参阅[调试 SharePoint 解决方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
2.  选择**F5**键以运行该项目并将其部署到 SharePoint。  
  
3.  在 SharePoint Web 页的顶部，打开**站点操作**菜单，然后选择**站点设置**。  
  
4.  下**站点操作**部分**站点设置**页上，选择**管理站点功能**链接。  
  
5.  上**功能**页上，选择**激活**按钮旁边**FeatureEvtTest Feature1**功能。  
  
6.  上**功能**页上，选择**停用**按钮旁边**FeatureEvtTest Feature1**功能，然后选择**停用此功能**确认链接停用该功能。  
  
7.  选择**主页**按钮。  
  
     请注意，在显示公告**公告**列表后停用该功能。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 创建事件接收器](../sharepoint/how-to-create-an-event-receiver.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  