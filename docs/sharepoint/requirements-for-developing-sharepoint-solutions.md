---
title: "开发 SharePoint 解决方案的需求 |Microsoft 文档"
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
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a29eee363f3ad886d9ea6a13ee43475fba2e9448
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>开发 SharePoint 解决方案的需求
  你可以使用 Visual Studio 中包含的 SharePoint 解决方案开发工具之前，必须在系统上安装以下先决条件：  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]或某一版本的 Visual Studio 应用程序生命周期管理 (ALM)。  
  
    -   请[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]或[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]功能，和/或文件名，在安装时[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
-   [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]在 64 位平台上安装[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]或 64 位[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。  
  
     或  
  
-   [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]在 64 位平台上安装[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]或 64 位[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。  
  
> [!NOTE]  
>  而只能服务器操作系统均获得官方支持由 SharePoint 中，允许两个客户端操作系统：[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]和[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]SP1。 有关详细信息，请参阅[SharePoint Server 2010 开发工作站安装指南](http://go.microsoft.com/fwlink/?LinkID=164557)。  
  
 业务数据连接 (BDC) 模型项目类型需要[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]系统上安装。  
  
 若要开发 Visual Studio 中的 SharePoint 解决方案，必须将 SharePoint 安装在与 Visual Studio 相同的计算机上。 此外，SharePoint 开发人员工具仅支持 SharePoint 独立配置;它们不支持场 （远程） 配置。  
  
> [!NOTE]  
>  Visual Studio 中的 SharePoint 项目仅支持[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。 如果你选择[!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)]将为新的 SharePoint 项目，它仍以目标[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]。  
  
 有关如何安装详细信息[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，请参阅[安装 Visual Studio](../install/install-visual-studio.md)。  
  
## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista 和 Windows 7 用户帐户控制 (UAC)  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]包含一个称为作为用户帐户控制 (UAC) 的安全功能。 若要开发 SharePoint 解决方案中的[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]上[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]和[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]系统，UAC 要求你运行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]作为系统管理员。 在桌面上，打开快捷菜单[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，然后选择**以管理员身份运行**。  
  
 若要配置要始终以管理员身份运行的桌面快捷方式，打开其快捷菜单，选择**属性**，选择**高级**按钮，，然后选择**以管理员身份运行**复选框。  
  
 有关详细信息，请参阅[了解和 Windows Vista 中配置用户帐户控制](http://go.microsoft.com/fwlink/?LinkID=156476)。 和[Windows 7 用户帐户控制](http://go.microsoft.com/fwlink/?LinkId=177523)。  
  
## <a name="sharepoint-permissions-considerations"></a>SharePoint 权限注意事项  
 若要开发 SharePoint 解决方案，你必须具有足够的权限来运行和调试 SharePoint 解决方案。 你可以测试 SharePoint 解决方案之前，请执行以下步骤以确保你具有必需的权限：  
  
1.  将你的用户帐户添加为系统上的管理员。  
  
2.  添加你的用户帐户作为 SharePoint 服务器场管理员。  
  
    1.  在 SharePoint 管理中心内，选择**管理场管理员组**链接。  
  
    2.  上**场管理员**页上，选择**新建**按钮。  
  
3.  将你的用户帐户添加到 WSS_ADMIN_WPG 组。  
  
## <a name="see-also"></a>另请参阅  
 [入门 &#40;Visual Studio &#41; 中的 SharePoint 开发](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  