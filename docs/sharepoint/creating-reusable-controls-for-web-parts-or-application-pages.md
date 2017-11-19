---
title: "为 Web 部件或应用程序页创建可重用控件 |Microsoft 文档"
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
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c094bea2376a1e76bec2f45dfb05bf689e6acc7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>为 Web 部件或应用程序页创建可重用控件
  在 Visual Studio 中，你可以创建可由 SharePoint 中运行的应用程序页和 Web 部件使用的自定义可重用控件。 这些控件称为用户控件。 用户控件是一种工作方式非常类似的 ASP.NET 网页的复合控件 — 可以将现有的 Web 服务器控件和标记添加到用户控件，并定义属性和控件的方法。 您然后可以将其嵌入在 ASP.NET Web 页中，它们充当一个单元。  
  
## <a name="creating-a-user-control"></a>创建用户控件  
 若要创建用户控件，添加**用户控件**到**空 SharePoint 项目**。 有关详细信息，请参阅[如何： 为 SharePoint 应用程序页或 Web 部件创建用户控件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)。  
  
 当你将添加**用户控件**项、 Visual Studio 在项目中，创建一个文件夹，然后将多个文件添加到的文件夹。 下表介绍每个文件。  
  
|文件|描述|  
|----------|-----------------|  
|用户控件文件|定义用户控件。 通过将控件和标记添加到此文件设计用户控件。|  
|代码文件|包含用户控件背后的代码。 添加代码以处理对此文件的事件。|  
|设计器代码文件|包含设计器所生成的代码，不应直接编辑。|  
  
## <a name="designing-the-user-control"></a>设计用户控件  
 通过使用 Visual Studio 中 Visual Web Developer 设计器设计用户控件。 此设计器随即出现在项目中打开用户控件文件并选择时**设计**选项卡。  

## <a name="consuming-the-user-control"></a>使用用户控件  
 直到将其包含在应用程序页或 Web 部件在 SharePoint 中不显示用户控件。  
  
 若要在应用程序页中包含用户控件，打开你想要添加 ASP.NET 用户控件的网页。 切换到设计视图中，然后在解决方案资源管理器中选择你自定义用户控件文件并将其拖到该页面。 ASP.NET 用户控件添加到页上，并设计器创建 @ Register 指令，所需的页后，可以识别该用户控件。 此外，你现在可以使用控件的公共属性和方法。  
  
 若要在 Web 部件中包含用户控件，请将用户控件添加到 Web 部件<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web 部件的代码文件中的集合。 下面的示例将添加到用户控件<xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A>Web 部件的集合。  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debugging-a-user-control"></a>调试用户控件  
 若要调试的用户控件，请确保用户控件包含在应用程序页或 Web 部件的 SharePoint 项目。 正如你将调试任何 Visual Studio 项目中的代码，然后可以调试在用户控件中的代码。  
  
 当你启动 Visual Studio 调试器时，Visual Studio 将打开 SharePoint 站点。  
  
 在 SharePoint 中，打开包含用户控件的应用程序页。 如果 Web 部件中包含用户控件，则将添加到 SharePoint 中的 Web 部件页的 Web 部件。  
  
 有关调试 SharePoint 项目的详细信息，请参阅[疑难解答 SharePoint 解决方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[如何：为 SharePoint 应用程序页或 Web 部件创建用户控件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|演示如何创建可由应用程序页和 SharePoint 中运行的 Web 部件使用的自定义的可重用控件。|  
  
  