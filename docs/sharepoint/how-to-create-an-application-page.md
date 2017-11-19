---
title: "如何： 创建的应用程序页 |Microsoft 文档"
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 80e85ca5da81b4e8dd715867a8819dbf292f527a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-application-page"></a>如何：创建应用程序页
  可以为一个或多个 SharePoint 网站创建 ASP.NET 网页。 在 SharePoint 中，这些页被称为应用程序页。 与站点页上，不同的应用程序页包含页后面运行的代码。 有关详细信息，请参阅[for SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
### <a name="to-create-an-application-page"></a>若要创建的应用程序页  
  
1.  在 Visual Studio 中打开或创建一个 SharePoint 项目。  
  
     有关详细信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在 **“解决方案资源管理器”**中，选择项目节点。  
  
3.  在菜单栏上，选择**项目**，**添加新项**。  
  
4.  在**添加新项**对话框框中，展开**SharePoint**节点，然后选择**2010年**项。  
  
5.  在 SharePoint 模板列表中，选择**应用程序页**。  
  
6.  在**名称**框中，为应用程序页上，指定一个名称，然后选择**添加**按钮。  
  
     Visual Studio 将添加到你的项目的几个文件夹和文件。 有关这些文件的详细信息，请参阅[for SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
     在**源**Visual Web Developer 设计器中，ASP.NET 页文件视图将显示。 你可以通过添加从控件设计页**工具箱**并将其置于内容占位符。 有关详细信息，请参阅[源视图、 网页设计器](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f)。  
  
7.  如果你要处理控件事件，请向应用程序页的代码文件添加代码。  
  
     如果展开 ASP.NET 页文件的节点并具有 .cs 或 .vb 扩展名（取决于项目语言），将显示代码文件。 有关如何创建的应用程序页的端到端示例，请参阅[演练： 创建 SharePoint 应用程序页](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)。  
  
## <a name="see-also"></a>另请参阅  
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [演练：创建 SharePoint 应用程序页](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  