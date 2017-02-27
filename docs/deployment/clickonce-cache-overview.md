---
title: "ClickOnce 缓存概述 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 应用程序, 缓存"
  - "ClickOnce 部署, 缓存"
  - "Windows 应用程序, ClickOnce 部署"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# ClickOnce 缓存概述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序（无论是本地安装的还是联机承载的）都存储在客户端计算机上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序缓存中。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 缓存是当前用户的 Documents and Settings 文件夹中 Local Settings 目录下的一系列隐藏目录。  此缓存保存所有应用程序文件，包括程序集、配置文件、应用程序和用户设置，以及数据目录。  该缓存还负责将该应用程序的数据目录迁移到最新版本。  有关数据迁移的更多信息，请参见 [在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
 通过为应用程序存储提供一个位置，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 从用户那里接管了管理应用程序物理安装的任务。  通过对所有应用程序及其不同版本的程序集和数据文件进行独立保存，缓存还有助于隔离应用程序。  例如，升级某个 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序时，该版本及其数据资源是通过它们自己在缓存中的目录提供的。  
  
## 缓存存储配额  
 联机承载的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序所能占用的空间量受配额限制，此配额限制了 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 缓存的大小。  缓存大小应用于所有用户的联机应用程序；单个部分信任的联机应用程序最多只能占用配额空间的一半。  安装的应用程序不受缓存大小的限制，因此，不受缓存限制的影响。  对于所有 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序，缓存只保留当前版本和之前安装的版本。  
  
 默认情况下，客户端计算机有 250 MB 的存储空间供联机 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序使用。  数据文件不计入该限制。  系统管理员可以通过改变注册表项 HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB 来增加或减小特定客户端计算机上的此配额。该注册表项是一个表示缓存大小（单位为千字节）的 DWORD 值。  例如，要将缓存大小减少到 50 MB，可以将该值更改为 51200。  
  
## 请参阅  
 [在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)