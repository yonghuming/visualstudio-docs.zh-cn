---
title: "“URL 选取器”对话框（Visual Studio 中的 SharePoint 开发）"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 开发, 设计器"
  - "Visual Studio 中的 SharePoint 开发, URL 选择器"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# “URL 选取器”对话框（Visual Studio 中的 SharePoint 开发）
  在URL选择器对话框中，您可以选择文件，如位于项目中或本地运行 SharePoint 的Server 上的母版页文件或图像文件。  
  
 在能够选择某个文件以设置属性时，将会显示该对话框。  通过选择**“属性”**窗口中各个属性旁边的省略号按钮 \(![ASP.NET 移动设计器中的省略号](../sharepoint/media/mwellipsis.png "ASP.NET 移动设计器中的省略号")\) 可打开此对话框。  此外，在将值分配给设计器的**“源”**视图中的某些特性时，省略号按钮将显示为 Intellisense 提示。  
  
## UIElement 列表  
 **项目文件夹**  
 显示项目中或本地运行 SharePoint 的Server 上定义的文件夹的列表。  选择展开按钮可显示子文件夹。  
  
 展开**“项目”**节点，以选择您项目中的文件。  若要在对话框中显示为可选项，您项目中的文件必须满足下列条件：  
  
-   该文件必须包含在映射文件夹中。  
  
-   该文件必须添加到解决方案包中。  
  
-   该文件不能位于另一个项目中。  
  
 若要引用未满足上述条件的文件，则必须手动输入该文件的路径。  
  
 展开 **服务器** 节点，选择位于本地服务器且运行 SharePoint 项目的文件。  要在对话框中显示为可选项，这些文件必须满足下列条件：  
  
-   该文件必须位于下列映射文件夹中：**“Images”**、**“Layouts”**或**“ControlTemplates”**。  
  
-   该文件不能位于 SharePoint 内容数据库中。  
  
 若要引用未满足上述条件的文件，则必须手动输入该文件的路径。  
  
 **文件夹内容**  
 显示选定文件夹中的文件的列表。  选择一个文件，然后选择**确定**按钮以关闭对话框，并将所选文件发送到调用它的进程。  
  
 **文件类型**  
 允许您从适合于正在执行的任务的文件的列表中进行选择。  
  
## 请参阅  
 [为 SharePoint 创建应用程序页](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [为 SharePoint 创建 Web 部件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [为 Web 部件或应用程序页创建可重用控件](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Visual Studio Web 开发环境内容映射](http://msdn.microsoft.com/zh-cn/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  