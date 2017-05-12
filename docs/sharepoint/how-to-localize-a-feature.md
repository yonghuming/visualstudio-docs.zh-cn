---
title: "如何：本地化功能"
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
  - "功能 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 本地化"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：本地化功能
  默认情况下，功能标题和说明使用硬编码的字符串值。  若要本地化功能标题和说明，请将字符串替换为引用本地化的资源的表达式。  
  
## 本地化功能  
  
#### 本地化功能  
  
1.  在**“解决方案资源管理器”**中，打开**“Feature1”**节点的快捷菜单，然后选择**“添加功能资源”**。  
  
2.  在 **添加资源** 对话框中，从列表选择 **固定语言** 作为默认语言功能资源文件的区域性。  
  
3.  为每种本地化语言重复先前的步骤，同时为本地化的功能资源文件选择所选的语言。  
  
     创建单独的功能资源文件：一个用于默认语言，另一个用于您希望支持的每种本地化语言。  
  
4.  在资源编辑器中打开每个资源文件，并输入所有字符串IDs及它们的值。  
  
     例如，在默认功能资源文件中，输入值为“My Feature Title”（我的功能标题）的标题的字符串ID ，以及值为“My Feature Description”（我的功能说明）的说明的另一个字符串ID 。  对于每个本地化的资源文件，使用默认功能资源文件中所使用的相同字符串ID ，但输入本地化的字符串。  
  
5.  在输入所有资源值后，打开的快捷菜单功能 \(例如，Feature1.feature\)，然后选择 **查看设计器** 以打开在功能设计器的功能。  
  
6.  若要本地化功能中的**“标题”**和**“说明”**字段，请使用以下格式在其框中输入值：  
  
     `$Resources:` *String ID*  
  
     例如，在**“功能标题”**框中输入 $Resources:Title，并在**“功能说明”**框中输入 $Resources:Description。  
  
     字符串ID必须与资源文件中使用的字符串 ID 匹配。  
  
7.  选择 F5 键生成并运行项目。  
  
8.  在 SharePoint 中，打开**“网站操作”**菜单，选择**“网站设置”**，然后在**“网站操作”**部分中选择**“管理网站功能”**链接。  
  
9. 在 SharePoint 中，更改默认显示语言。  
  
     本地化的功能标题和说明将出现在应用程序中。  若要显示本地化资源，SharePoint 服务器必须安装了与该资源文件的区域特点相匹配的语言包。  
  
## 请参阅  
 [本地化 SharePoint 解决方案](../sharepoint/localizing-sharepoint-solutions.md)   
 [如何：添加资源文件](../sharepoint/how-to-add-a-resource-file.md)   
 [如何：本地化 ASPX 标记](../sharepoint/how-to-localize-aspx-markup.md)   
 [如何：本地化代码](../sharepoint/how-to-localize-code.md)  
  
  