---
title: "生成和调试 SharePoint 解决方案"
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
  - "Visual Studio 中的 SharePoint 开发, 生成和调试"
  - "Visual Studio 中的 SharePoint 开发, 调试"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# 生成和调试 SharePoint 解决方案
  通常，生成和调试 SharePoint 解决方案与生成和调试 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中其他类型的项目相同。  本节内容的主题解释确实存在的差异。  
  
## SharePoint 解决方案的项目输出  
 生成 SharePoint 解决方案时将创建程序集和一个解决方案包 \(.wsp\) 文件。  下表显示了这些文件在生成过程中的位置。  
  
|生成项|输出文件夹|  
|---------|-----------|  
|程序集、程序数据库 \(PDB\) 和 .wsp 文件。|*ProjectName*\\ bin \\ debug 或 *ProjectName*\\ bin \\ release|  
|SharePoint 项目项文件。|*ProjectName*\\ pkg \\ debug 或 *ProjectName*\\ pkg \\ release|  
|生成中间文件。|*ProjectName*\\ obj \\ debug 或 *ProjectName*\\ obj \\ release|  
|包中间文件。|*ProjectName*\\ pkgobj \\ debug 或 *ProjectName*\\ pkgobj \\ release|  
  
## 生成 SharePoint 解决方案  
 若要生成 SharePoint 解决方案，开发计算机必须安装了正确版本的 SharePoint 服务器。  否则，生成 SharePoint 解决方案将与生成 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中其他类型的项目相同。  有关详细信息，请参阅[如何：生成 SharePoint 解决方案](../sharepoint/how-to-build-sharepoint-solutions.md)。  
  
## 调试和测试 SharePoint 解决方案  
 在调试之前，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 会将 .wsp 包复制到 SharePoint 服务器，激活网站和 Web 范围的功能，并在某些情况下启动项目。  在某些情况下，您可能必须手动打开项目。  有关更多信息，请参见[SharePoint 解决方案疑难解答](../sharepoint/troubleshooting-sharepoint-solutions.md)和[调试 SharePoint 解决方案](../sharepoint/debugging-sharepoint-solutions.md)。  
  
## 使用 ALM 功能调试和验证 SharePoint 解决方案  
 Visual Studio ALM 功能例如单元测试和 IntelliTrace 更准确查明 SharePoint 解决方案中的问题。  分析可以查找并确定在 SharePoint 解决方案的性能问题区域。  有关更多信息，请参见[验证和调试 SharePoint 代码](../sharepoint/verifying-and-debugging-sharepoint-code.md)和[分析 SharePoint 应用程序的性能](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)。  
  
## 生成过程期间的安全  
 若要打包或部署 SharePoint 解决方案，[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 必须具有将文件复制到 SharePoint 服务器的权限。  必须以提升的进程的形式运行 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，并且您的用户帐户必须是 SharePoint 服务器上的网站集管理员。  此外，您必须指定您的项目是沙盒解决方案还是场解决方案。  有关详细信息，请参阅[沙盒解决方案与场解决方案之间的差异](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)。  
  
## 使用“清理”命令  
 如果在 SharePoint 服务器上安装了 SharePoint 解决方案进行调试，则**“清理”**命令不会卸载解决方案，  而是必须通过 SharePoint 配置停用功能。  
  
## 请参阅  
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)   
 [使用服务器资源管理器浏览 SharePoint 连接](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [打包和部署 SharePoint 解决方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  