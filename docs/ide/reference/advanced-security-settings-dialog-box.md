---
title: "“高级安全设置”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.err.debug_in_zone_no_hostproc"
  - "vs.err.debug_in_zone_no_hostproc:11310"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "“高级安全设置”对话框"
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “高级安全设置”对话框
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

此对话框可用于指定与在区域中调试相关的安全设置。  
  
 若要访问此对话框，请在**“解决方案资源管理器”**中选择项目节点，然后在**“项目”**菜单上单击**“属性”**。  当**“项目设计器”**出现时，单击**“安全性”**选项卡。  在**“安全性”**页上，选择**“启用 ClickOnce 安全设置”**，单击**“这是不完全可信的应用程序”**，然后单击**“高级”**。  
  
## UIElement 列表  
 **使用所选的权限集调试此应用程序**  
 如果选中此复选框，则调试过程中使用**“安全”**页上所选择的权限集。  默认情况下，该选项是选中的。  
  
 为了可以在安全区域中进行调试，必须启用此选项和**“启用 Visual Studio 宿主进程”**选项（在**“项目设计器”**的**“调试”**页上可用）。  
  
 对于 WPF Web 浏览器应用程序项目，选中并禁用**“使用选定权限集调试此应用程序”**选项。  
  
 **授予应用程序对其源站点的访问权**  
 如果选中此复选框，则应用程序可以访问发布其的网站或服务器共享。  默认情况下，该选项是选中的。  
  
 **调试此应用程序，就如同它是从以下 URL 位置下载的一样**  
 如果必须允许应用程序访问对应于您在**“发布”**页上指定的**“安装 URL”**的网站或服务器共享，请在此处键入该 URL。  此选项仅在选中**“授予应用程序对其源站点的访问权”**时才可用。  
  
## 请参阅  
 [”项目设计器“ \-\>“安全”页](../../ide/reference/security-page-project-designer.md)