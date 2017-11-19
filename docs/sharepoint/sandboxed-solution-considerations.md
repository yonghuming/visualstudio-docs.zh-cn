---
title: "沙盒解决方案注意事项 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4598b100572bb47fd537e8edad927d78b4f1550
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *沙盒解决方案*是使站点集合用户能够上载其自己的自定义代码的解决方案的 Microsoft SharePoint 2010 中的功能。 常见的沙盒解决方案是将 Web 部件添加自己的用户。  
  
 沙盒的 SharePoint 应用程序在有权访问 Web 场的有限一部分使用安全的监视过程中运行。 Microsoft SharePoint 2010 结合使用的功能、 解决方案库、 监视的解决方案和验证框架来启用沙盒解决方案。  
  
## <a name="specifying-project-trust-level"></a>指定项目的信任级别  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]支持通过布尔项目属性的沙盒解决方案调用*沙盒解决方案*。 可以随时在项目中，设置此属性或可以指定当创建的项目中**SharePoint 自定义向导**。  
  
> [!NOTE]  
>  更改*沙盒解决方案*项目将在创建后的属性可能会导致验证错误。  
  
 如果，解决方案将被视为场范围解决方案*沙盒解决方案*属性设置为**false**或你选择**部署为场解决方案**选项。 但是，该解决方案不会被视为场解决方案如果*沙盒解决方案*属性设置为**true**或你选择**部署为沙盒解决方案**在向导中的选项。  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint 站点层次结构  
 若要了解如何沙盒解决方案工作，它有助于了解作用域中的 SharePoint 站点是层次结构。 顶部的元素称为 Web 场和其他元素都从属于它：  
  
 Web 场  
  
 Web 应用程序 A  
  
 站点集合 A1  
  
 站点 A1a  
  
 Web 应用程序 B  
  
 站点集合 B1  
  
 站点 B1a  
  
 站点 B1b  
  
 网站集 B2  
  
 站点 B2a  
  
 如你所见，Web 场可包含一个或多个 Web 应用，又可以包含一个或多个网站集，可以有子站点，并且其他操作。 对一个站点集合产生哪些影响仅站点集合和任何其他更改。 但是，在 Web 场级别所做的更改会影响为场的所有网站集中。  
  
 Windows SharePoint Services (WSS) 3.0，可将解决方案部署到的场级别，但[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]可部署为场级别 （场解决方案） 或网站集级别 （沙盒解决方案）。  
  
## <a name="why-sandboxed-solutions"></a>为什么沙盒解决方案？  
 在 WSS 3.0 中，解决方案可能只能部署到的场级别。 这意味着影响整个 Web 场和的所有其他网站集和其下运行的应用程序，无法部署可能有害或不稳定的解决方案。 但是，通过使用沙盒解决方案，可以将你的解决方案部署的场，特定站点集合子区域。 若要提供附加保护，解决方案的程序集不是加载到主[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]进程 (w3wp.exe)。 相反，它被加载到单独的进程 (SPUCWorkerProcess.exe)。 此过程进行监视，并实现配额和限制，以防止场中出现执行有害的活动，如运行消耗 CPU 周期的紧凑循环的沙盒解决方案。  
  
## <a name="site-collection-solution-gallery"></a>网站集解决方案库  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 包含一项名为“网站集解决方案库”的功能。 你可以访问此功能，SharePoint 2010 管理中心页中，或通过打开**站点操作**菜单上，选择**站点设置**，然后选择**解决方案**链接下**库**SharePoint 站点中。 解决方案库是存储库的解决方案，使站点集合管理员能够管理其网站集中的解决方案。  
  
 解决方案库是存储在根 SharePoint 网站的 Web 文档库。 解决方案库替换站点模板，并支持解决方案包。 上载的 SharePoint 解决方案包 (.wsp) 文件时，它是为沙盒解决方案中进行处理。  
  
## <a name="sandboxed-solution-limitations"></a>沙盒解决方案限制  
 部署时沙盒解决方案，可用于它的 SharePoint 功能的数组是限制以减少它可以具有任何安全漏洞。 某些这些限制包括：  
  
-   沙盒解决方案都具有可部署解决方案元素提供给他们的受限的子集。 可能易受攻击的 SharePoint 项目模板，如站点定义和工作流，将不可用。  
  
-   SharePoint 运行沙盒解决方案中的代码的进程 (SPUCWorkerProcess.exe) 独立于主[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]应用程序池 (w3wp.exe) 进程。  
  
-   映射的文件夹不能添加到项目。  
  
-   中的类型[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Microsoft.Office.Server 不能在沙盒解决方案的程序集。 此外，仅在类型[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]Microsoft.SharePoint 可以沙盒解决方案中使用的程序集。  
  
 务必要注意为沙盒解决方案 SharePoint 服务器; 没有任何影响该指定 SharePoint 解决方案它只确定如何将 SharePoint 项目部署到 SharePoint 从[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和哪些程序集它绑定到。 它不会影响生成的.wsp 文件中，而该.wsp 文件的直接关联到任何数据*沙盒解决方案*属性。  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>功能和沙盒解决方案中的元素  
 沙盒解决方案支持的以下功能和元素：  
  
-   内容的类型字段  
  
-   自定义操作  
  
-   声明性工作流  
  
-   事件接收器  
  
-   功能标注  
  
-   列表定义  
  
-   列表实例  
  
-   模块/文件  
  
-   导航  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   派生自的所有 Web 部件的支持`System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Web 部件  
  
-   WebTemplate 功能元素 （而不是 Webtemp.xml)  
  
-   可视 Web 部件  
  
 沙盒解决方案不支持以下功能和元素：  
  
-   应用程序页  
  
-   自定义操作组  
  
-   场设限功能  
  
-   `HideCustomAction` 元素  
  
-   Web 应用程序范围的功能  
  
-   使用代码的工作流  
  
## <a name="see-also"></a>另请参阅  
 [差异沙盒解决方案与场解决方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  