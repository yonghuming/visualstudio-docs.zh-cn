---
title: "SharePoint 解决方案的安全性 | Microsoft Docs"
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
  - "安全性 [Visual Studio 中的 SharePoint 开发]"
  - "Visual Studio 中的 SharePoint 开发, 安全性"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint 解决方案的安全性
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 包含了以下功能来帮助增强 SharePoint 应用程序的安全性。  
  
## 安全控制项  
 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中创建的每个 SharePoint 项目项都有一个**“安全控制项”**属性，该属性表示安全控件集合。  利用其**“安全”**子属性可以指定您视为安全的控件。  有关更多信息，请参见 [在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 和 [指定安全的 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177521)。  
  
## AllowPartiallyTrustedCallers 特性  
 默认情况下，只有运行时代码访问安全性 \(CAS\) 系统完全信任的应用程序才能访问共享的托管代码程序集。  通过用 AllowPartiallyTrustedCallers 特性标记完全信任的程序集，将允许部分信任的程序集访问该程序集。  
  
 AllowPartiallyTrustedCallers 特性将添加到未部署到系统全局程序集缓存 \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) 的任何 SharePoint 解决方案。  其中包括沙盒解决方案或部署到 SharePoint 应用程序 Bin 目录的解决方案。  有关更多信息，请参见 [生成 . 1 Microsoft .NET Framework 的安全更改](http://go.microsoft.com/fwlink/?LinkId=177515) 和 [在 SharePoint Foundation 中部署 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
## “安全应对脚本”属性  
 “脚本注入”是指将潜在恶意代码插入控件或网页。  为了帮助 SharePoint 2010 网站抵御脚本注入，参与者默认情况下无法查看或编辑 Web 部件或其属性。  此行为由一个名为“SafeAgainstScript”的 SafeControl 特性控制。  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，在项目项的**“安全控制项”**子属性**“安全应对脚本”**中设置此特性。  有关更多信息，请参见[在项目项中提供打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)和[如何：将控件标记为安全控件](../sharepoint/how-to-mark-controls-as-safe-controls.md)。  
  
## Vista 和 Windows 7 用户帐户控制  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 包含一个名为“用户帐户控制”\(UAC\) 的安全功能。  若要在 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 系统上开发 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中的 SharePoint 解决方案，UAC 将要求您以管理员身份运行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  从**“启动”**菜单，打开 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的快捷菜单，然后选择 **以管理员身份运行**。  
  
 若要配置 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 快捷键总是以管理员身份运行，打开其快捷菜单中，选择 **属性**，选择 **高级** 按钮，在**属性** 对话框中，然后选择 **以管理员身份运行** 复选框。  
  
 有关更多信息，请参见[了解和配置 Windows Vista 中的用户帐户控制](http://go.microsoft.com/fwlink/?LinkID=156476)和[Windows 7用户账户控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## SharePoint 权限注意事项  
 若要开发 SharePoint 解决方案，您必须拥有运行和调试 SharePoint 解决方案的足够权限。  在您可以测试 SharePoint 解决方案之前，请执行以下步骤以确保您拥有必需的权限：  
  
1.  添加您的用户帐户作为系统上的管理员。  
  
2.  添加您的用户帐户作为 SharePoint 服务器的服务器场管理员。  
  
    1.  在 SharePoint 2010 管理中心中，选择**“管理服务器场管理员组”**链接。  
  
    2.  在 **服务器场管理员** 页中，选择 **新建** 菜单选项  
  
3.  将用户帐户添加到 WSS\_ADMIN\_WPG 组。  
  
## 其他安全资源  
 有关安全性问题的更多信息，请参见以下内容。  
  
### Visual Studio 安全性  
  
-   [安全和用户权限](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [本机代码和 .NET Framework 代码的安全性](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [.NET Framework 中的安全性](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### SharePoint 安全性  
  
-   [SharePoint Foundation 管理和安全](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint 安全资源中心](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [获得在 SharePoint Foundation 的 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [提高 Web 应用程序的安全性：威胁及对抗措施](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### 一般安全性  
  
-   [MSDN安全开发生命周期](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [生成安全的 ASP.NET 应用程序：身份验证、授权和安全通信](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [开发 SharePoint 解决方案的要求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  