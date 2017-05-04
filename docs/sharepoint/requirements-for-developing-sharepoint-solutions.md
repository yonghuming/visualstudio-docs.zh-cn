---
title: "开发 SharePoint 解决方案的要求 | Microsoft Docs"
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
  - "Visual Studio 中的 SharePoint 开发, 系统必备"
  - "Visual Studio 中的 SharePoint 开发, 要求"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 开发 SharePoint 解决方案的要求
  必须先在系统上安装以下系统必备组件，然后才能使用Visual Studio中包括的 SharePoint 解决方案开发工具：  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]或 Visual Studio Application Lifecycle Management \(ALM\) 的某个版本。  
  
    -   在安装 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 时，为 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 功能，或者为二者。  
  
-   安装在 64 位 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 或 64 位 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 上的 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。  
  
     或  
  
-   安装在 64 位 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] 或 64 位 [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 上的 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]。  
  
> [!NOTE]  
>  仅当服务器操作系统由 SharePoint 时正式支持时，两个客户端操作系统允许：[!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 和 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1。  有关详细信息，请参阅 [SharePoint Server 2010 开发工作区域安装指南](http://go.microsoft.com/fwlink/?LinkID=164557)。  
  
 业务数据连接 \(BDC\) 模型项目类型要求在系统上安装 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。  
  
 若要在 Visual Studio 中开发 SharePoint 解决方案，您必须在安装 Visual Studio 的计算机上安装 SharePoint。  此外，SharePoint 开发人员工具仅支持 SharePoint 独立配置，而不支持服务器场（远程）配置。  
  
> [!NOTE]  
>  在 Visual Studio中，SharePoint 项目仅支持 [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。  如果为新的 SharePoint 项目选择 [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)]，则它仍将面向 [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。  
  
 有关如何安装 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 的更多信息，请参见[安装 Visual Studio](../Topic/Installing%20Visual%20Studio.md)。  
  
## Vista 和 Windows 7 用户帐户控制 \(UAC\)  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 包含一个名为“用户帐户控制”\(UAC\) 的安全性功能。  为了在 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 和 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 系统上的 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中开发 SharePoint 解决方案，UAC 将要求您以系统管理员身份运行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  在桌面上，打开 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]的快捷菜单，然后选择 **以管理员身份运行**。  
  
 若要将桌面快捷方式配置为始终以管理员身份运行，请打开快捷菜单，单击**“属性”**，再单击**“高级”**按钮，然后选择**“以管理员身份运行”**复选框。  
  
 有关更多信息，请参见[了解和配置 Windows Vista 中的用户帐户控制](http://go.microsoft.com/fwlink/?LinkID=156476)和[Windows 7用户账户控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## SharePoint 权限注意事项  
 若要开发 SharePoint 解决方案，您必须拥有运行和调试 SharePoint 解决方案的足够权限。  在您可以测试 SharePoint 解决方案之前，请执行以下步骤以确保您拥有必需的权限：  
  
1.  添加您的用户帐户作为系统上的管理员。  
  
2.  添加您的用户帐户作为 SharePoint 服务器的服务器场管理员。  
  
    1.  在 SharePoint 管理中心中，选择**“管理服务器场管理员组”**链接。  
  
    2.  在 **服务器场管理员** 页面上，选择 **新建** 按钮。  
  
3.  将用户帐户添加到 WSS\_ADMIN\_WPG 组。  
  
## 请参阅  
 [入门（Visual Studio 中的 SharePoint 开发）](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  