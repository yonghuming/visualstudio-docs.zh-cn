---
title: "SharePoint 解决方案的安全性 |Microsoft 文档"
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
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c57626827be8487d19cd546bc31bd32b0859cec7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint 解决方案的安全性
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]包含以下功能来帮助提高的 SharePoint 应用程序的安全性。  
  
## <a name="safe-control-entries"></a>安全控件项  
 在中创建的每个 SharePoint 项目项[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]具有**安全控件项**表示一个安全的属性控制集合。 其**安全**子属性，可指定你考虑安全的控件。 有关详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)和[指定安全 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177521)。  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 属性  
 默认情况下，仅由运行时代码访问安全性 (CAS) 系统完全受信任的应用程序可以访问共享的托管的代码程序集。 标记具有 AllowPartiallyTrustedCallers 属性的完全受信任程序集允许部分受信任的程序集来访问它。  
  
 AllowPartiallyTrustedCallers 属性添加到未部署系统全局程序集缓存到任何 SharePoint 解决方案 ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 这包括沙盒解决方案或解决方案部署到 SharePoint 应用程序 Bin 目录。 有关详细信息，请参阅[Microsoft.NET framework 的版本 1 安全更改](http://go.microsoft.com/fwlink/?LinkId=177515)和[SharePoint Foundation 中部署 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
## <a name="safe-against-script-property"></a>安全应对脚本属性  
 *脚本注入*是指将潜在恶意代码插入控件或网页。 为了帮助保护对脚本注入的 SharePoint 2010 站点，contributors （参与者） 不能查看或编辑默认情况下的 Web 部件或其属性。 通过调用 SafeAgainstScript SafeControl 特性控制此行为。 在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，将此属性设置中的项目项**安全控件项**子属性**安全应对脚本**。 有关详细信息，请参阅[提供打包和部署信息在项目项中](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)和[如何： 为安全控件的标记控件](../sharepoint/how-to-mark-controls-as-safe-controls.md)。  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista 和 Windows 7 的用户帐户控制  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]包含一个名为用户帐户控制 (UAC) 的安全功能。 若要开发 SharePoint 解决方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]系统，UAC 要求你运行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]作为系统管理员。 从**启动**菜单上，打开快捷菜单[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然后选择**以管理员身份运行**。  
  
 若要配置[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]快捷方式，以便始终以管理员身份运行，打开其快捷菜单，选择**属性**，选择**高级**按钮**属性**对话框中，然后选择**以管理员身份运行**复选框。  
  
 有关详细信息，请参阅[了解和 Windows Vista 中配置用户帐户控制](http://go.microsoft.com/fwlink/?LinkID=156476)。 和[Windows 7 用户帐户控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## <a name="sharepoint-permissions-considerations"></a>SharePoint 权限注意事项  
 若要开发 SharePoint 解决方案，你必须具有足够的权限来运行和调试 SharePoint 解决方案。 你可以测试 SharePoint 解决方案之前，请执行以下步骤以确保你具有必需的权限：  
  
1.  将你的用户帐户添加为系统上的管理员。  
  
2.  添加你的用户帐户作为 SharePoint 服务器场管理员。  
  
    1.  在 SharePoint 2010 管理中心，选择**管理场管理员组**链接。  
  
    2.  上**场管理员**页上，选择**新建**菜单选项  
  
3.  将你的用户帐户添加到 WSS_ADMIN_WPG 组。  
  
## <a name="additional-security-resources"></a>其他安全资源  
 有关安全问题的详细信息，请参阅以下资源。  
  
### <a name="visual-studio-security"></a>Visual Studio 安全  
  
-   [安全和用户权限](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [在本机和.NET Framework 代码中的安全](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [.NET Framework 中的安全性](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>SharePoint 安全  
  
-   [SharePoint Foundation 管理和安全](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint 安全资源中心](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [保护 SharePoint Foundation 中的 Web 部件](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [改进的 Web 应用程序安全性： 威胁和对策](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>常规安全  
  
-   [MSDN 安全开发生命周期](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [生成安全的 ASP.NET 应用程序： 身份验证、 授权和安全通信](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [开发 SharePoint 解决方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  