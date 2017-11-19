---
title: "生成和调试 SharePoint 解决方案 |Microsoft 文档"
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
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7582b0bcef8a97de14fb3b931745d6dcc21fa876
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="building-and-debugging-sharepoint-solutions"></a>生成和调试 SharePoint 解决方案
  通常情况下，生成和调试 SharePoint 解决方案是生成和调试其他类型的项目中相同[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 本部分的主题介绍存在的差异。  
  
## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 解决方案的的项目输出  
 构建 SharePoint 解决方案创建程序集和解决方案包 (.wsp) 文件。 下表显示在生成期间这些文件的位置。  
  
|生成项目|输出文件夹|  
|----------------|-------------------|  
|程序集、 程序数据库 (PDB)，以及.wsp 文件。|*ProjectName*\bin\debug 或*ProjectName*\bin\release|  
|SharePoint 项目项文件。|*ProjectName*\pkg\debug 或*ProjectName*\pkg\release|  
|生成中间文件。|*ProjectName*\obj\debug 或*ProjectName*\obj\release|  
|包中间文件。|*ProjectName*\pkgobj\debug 或*ProjectName*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>构建 SharePoint 解决方案  
 若要生成 SharePoint 解决方案，开发计算机必须安装 SharePoint 服务器的正确版本。 否则，构建 SharePoint 解决方案等同于生成其他类型的项目中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 有关详细信息，请参阅[如何： 生成 SharePoint 解决方案](../sharepoint/how-to-build-sharepoint-solutions.md)。  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>调试和测试 SharePoint 解决方案  
 在调试时之前,[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]将.wsp 包复制到 SharePoint 服务器、 激活网站和 Web 范围的功能，并在某些情况下，启动项目。 在某些情况下，您可能必须手动打开项目。 有关详细信息，请参阅[疑难解答 SharePoint 解决方案](../sharepoint/troubleshooting-sharepoint-solutions.md)和[调试 SharePoint 解决方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>使用 ALM 功能调试和验证 SharePoint 解决方案  
 Visual Studio ALM 功能（例如单元测试和 IntelliTrace）可以更准确地查明 SharePoint 解决方案中的问题。 通过分析，您可以查找并确定 SharePoint 解决方案中的性能问题区域。 有关详细信息，请参阅[验证和调试 SharePoint 代码](../sharepoint/verifying-and-debugging-sharepoint-code.md)和[分析 SharePoint 应用程序性能](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。  
  
## <a name="security-during-the-build-process"></a>在生成过程中的安全  
 若要打包或部署 SharePoint 解决方案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]必须有权将文件复制到 SharePoint 服务器。 必须运行[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提升的进程，以及你的用户帐户必须是 SharePoint 服务器上的站点集合管理员。 此外，你必须指定你的项目是否沙盒解决方案或场解决方案。 有关详细信息，请参阅[差异之间沙盒解决方案和场解决方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## <a name="using-the-clean-command"></a>使用“清除”命令  
 在调试时，使用 SharePoint 服务器上安装 SharePoint 解决方案时**清理**命令不会卸载该解决方案。 相反，你必须先停用通过 SharePoint 配置的功能。  
  
## <a name="see-also"></a>另请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [使用服务器资源管理器浏览 SharePoint 连接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  