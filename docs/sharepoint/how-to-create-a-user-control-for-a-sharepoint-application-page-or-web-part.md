---
title: "如何：为 SharePoint 应用程序页或 Web 部件创建用户控件 | Microsoft Docs"
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
  - "用户控件 [Visual Studio 中的 SharePoint 开发], 添加"
  - "用户控件 [Visual Studio 中的 SharePoint 开发], 创建"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：为 SharePoint 应用程序页或 Web 部件创建用户控件
  可以创建为 SharePoint 解决方案提供自定义功能的自定义用户控件，可以重用项目中的功能。  在 web 部件或应用程序页面中包含用户控件，添加其他 ASP.NET 控件和 SharePoint 控件，定义控件的属性和方法。  有关用户控件的详细信息，请参见 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) 和 [SharePoint中的用户控件和服务器控件](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx) 。  
  
### 为 SharePoint 创建用户控件  
  
1.  在 Visual Studio 中打开或创建一个 SharePoint 项目。  
  
     请参见 [SharePoint 项目和项目项模板](../sharepoint/sharepoint-project-and-project-item-templates.md)。  
  
2.  在“解决方案资源管理器”中，选择项目节点。  
  
3.  在菜单栏上，依次选择“项目”、“添加新项”。  
  
     **“添加新项”**对话框打开。  
  
4.  在“已安装”  窗格中，选择“ Office\/SharePoint” 节点。  
  
5.  在 SharePoint 模板列表中，选择”用户控件“ \(仅在解决方案中\) 。  
  
    > [!NOTE]  
    >  用户控件仅适用于解决方案。  
  
6.  在“名称”框中，指定用户控件，然后选中“添加”按钮。  
  
     Visual Studio 将向项目中添加几个文件夹和文件。  有关这些文件的更多信息，请参见 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)。  
  
     默认情况下，用户控件文件显示在 Visual Web Developer 设计器的**“源”**视图中。  在此视图中，您可以编辑该控件的 XML 标记。  如果要通过从“工具箱”中拖动控件来可视化地设计控件，请切换到“设计”视图。  请参见 [NIB: Design View, Web Page Designer](http://msdn.microsoft.com/zh-cn/d8f2270a-357d-40a4-9b39-1a3f2366216d)。  
  
7.  如果要在控件中处理发生的事件，请将代码添加到用户控件的代码文件。  
  
     此文件将显示在用户控件文件下的“解决方案资源管理器” 中，具有 .cs 或 .vb 扩展名取决于项目的语言。  
  
## 请参阅  
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  