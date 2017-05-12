---
title: "如何：创建应用程序页"
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
  - "应用程序页 [Visual Studio 中的 SharePoint 开发], 添加"
  - "应用程序页 [Visual Studio 中的 SharePoint 开发], 创建"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：创建应用程序页
  您可以为一个或多个 SharePoint 站点创建 ASP.NET 网页。  在 SharePoint 中，这些页称为应用程序页。  与网站页面不同，应用程序页包含在页背后运行的代码。  有关详细信息，请参阅[为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
### 创建应用程序页  
  
1.  在 Visual Studio 中打开或创建一个 SharePoint 项目。  
  
     有关详细信息，请参阅[SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在**“解决方案资源管理器”**中，选择项目节点。  
  
3.  在菜单栏上，依次选择**“项目”**、**“添加新项”**。  
  
4.  在“添加新项”对话框中，展开“SharePoint” 节点，然后选择“2010”项。  
  
5.  在 SharePoint 模板列表中，选择 **应用程序页**。  
  
6.  在“名称”框中，指定应用程序页的名称，然后选中“添加”按钮。  
  
     Visual Studio 将向项目中添加几个文件夹和文件。  有关这些文件的更多信息，请参见 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)。  
  
     在Visual Web 开发者设计器的**源**视图，ASP.NET页文件出现。  您可以通过从**“工具箱”**添加控件和将它们放在内容占位符上来设计页。  有关更多信息，请参见[网页设计器的“源”视图](http://msdn.microsoft.com/zh-cn/5911396b-fe51-4150-9ff1-b085f812862f)。  
  
7.  如果您要处理控件事件，请向应用程序页的代码文件添加代码。  
  
     如果展开 ASP.NET 页文件的节点并具有 .cs 或 .vb 扩展名，代码文件取决于项目的语言显示。  有关如何创建应用程序页的端对端示例，请参见[演练：创建 SharePoint 应用程序页](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
## 请参阅  
 [Visual Studio Web 开发环境内容映射](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [演练：创建 SharePoint 应用程序页](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  