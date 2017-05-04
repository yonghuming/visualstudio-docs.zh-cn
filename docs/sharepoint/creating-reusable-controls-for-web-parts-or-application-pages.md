---
title: "为 Web 部件或应用程序页创建可重用控件 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 用户控件"
  - "用户控件 [Visual Studio 中的 SharePoint 开发], 创建"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 为 Web 部件或应用程序页创建可重用控件
  通过 Visual Studio，您可以创建可由在 SharePoint 中运行的应用程序页和 Web 部件使用的自定义可重用控件。  这些控件称作用户控件。  有关用户控件的更多信息，请参见[ASP.NET User Controls](http://msdn.microsoft.com/library/5e601b3d-bb16-4dbe-9e35-7e92a34565ca)。  
  
## 创建用户控件  
 若要创建用户控件，请向一个**“空 SharePoint 项目”**中添加**“用户控件”**。  有关详细信息，请参阅[如何：为 SharePoint 应用程序页或 Web 部件创建用户控件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)。  
  
 添加**“用户控件”**项后，Visual Studio 将在您的项目中创建一个文件夹，然后向该文件夹中添加几个文件。  下表介绍每个文件。  
  
|文件|说明|  
|--------|--------|  
|用户控件文件|定义用户控件。  通过向此文件添加控件和标记设计用户控件。|  
|代码文件|包含用户控件背后的代码。  请向此文件添加用于处理事件的代码。|  
|设计器代码文件|包含由设计器生成的代码，不应直接编辑此文件。|  
  
## 设计用户控件  
 可以使用 Visual Studio 中的 Visual Web Developer 设计器设计用户控件。  当您打开该项目的用户控件文件并选择 **设计** 选项卡时，显示此设计器。。  有关使用此设计器的更多信息，请参见[Visual Studio Web 开发环境内容映射](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)。  
  
## 使用用户控件  
 只有在将用户控件包括在应用程序页或 Web 部件中时，用户控件才会显示在 SharePoint 中。  
  
 若要将用户控件包含在应用程序页中，请将 [@ Register](http://msdn.microsoft.com/zh-cn/66f34922-be41-4e36-9dc8-1774d85311d1) 指令添加到应用程序页，然后在该页中的一个或多个内容占位符内声明该用户控件。  有关如何在标准 ASP.NET 网页中完成此任务的示例，请参见[How to: Include a User Control in an ASP.NET Web Page](http://msdn.microsoft.com/library/7c3bfd74-846c-4b88-b1ef-45d75860af92)。  
  
 若要在 Web 部件中包括某个用户控件，请将该用户控件添加到 Web 部件代码文件中的 Web 部件 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 集合。  下面的示例将一个用户控件添加到 Web 部件的 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 集合。  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## 调试用户控件  
 若要调试某个用户控件，请确保该用户控件包括在 SharePoint 项目的应用程序页或 Web 部件中。  然后，可以调试用户控件中的代码，就像调试任何 Visual Studio 项目中的代码一样。  
  
 当您启动 Visual Studio 调试器时，Visual Studio 将打开 SharePoint 站点。  
  
 在 SharePoint 中，打开包括用户控件的应用程序页。  如果用户控件包括在某个 Web 部件中，请将该 Web 部件添加到 SharePoint 中的 Web 部件页。  
  
 有关调试 SharePoint 项目的更多信息，请参见[SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[如何：为 SharePoint 应用程序页或 Web 部件创建用户控件](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|演示如何创建可由在 SharePoint 中运行的应用程序页和 Web 部件使用的自定义的可重用控件。|  
|[使用 Visual Web Developer](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|说明如何使用在项目中打开网页时出现的设计器。|  
  
  