---
title: "ClickOnce 缓存概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1aa73140760f161971f30e4232658b18453f233f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-cache-overview"></a>ClickOnce 缓存概述
所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，无论它们是以本地方式安装还是联机，承载存储中的客户端计算机上[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序*缓存*。 A[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]缓存是一系列的当前用户的 Documents and Settings 文件夹的本地设置目录下隐藏的目录。 此缓存包含应用程序的所有文件，包括程序集、 配置文件、 应用程序和用户设置和数据目录。 缓存程序还负责迁移到最新版本的应用程序的数据目录。 有关数据迁移的详细信息，请参阅[访问本地数据和 ClickOnce 应用程序中的远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
 通过提供用于应用程序存储的单个位置[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]接管用户管理应用程序的物理安装的任务。 缓存还有助于通过保留的程序集和数据文件的所有应用程序隔离应用程序和从另一个单独的及其不同版本。 例如，当升级[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序中，使用自己的目录缓存中提供版本和其数据资源。  
  
## <a name="cache-storage-quota"></a>缓存存储配额  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]联机承载的应用程序被限制他们可以占用的空间量受约束的大小配额[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]缓存。 缓存大小适用于所有用户的联机应用程序;单个的部分受信任、 联机应用程序仅限于占用一半配额的空间。 已安装应用程序不受缓存大小并不会抵消缓存限制。 所有[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序，缓存保留仅的当前版本和以前安装的版本。  
  
 默认情况下，客户端计算机具有 250 MB 的存储联机[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 数据文件不计入此限制。 系统管理员可以放大或缩小通过更改注册表项，HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB，这是一个 DWORD 值的特定客户端计算机上的此配额表示的缓存大小，以千字节为单位。 例如，若要减少到 50 MB 的缓存大小，将为 51200 更改此值。  
  
## <a name="see-also"></a>另请参阅  
 [在 ClickOnce 应用程序中访问本地数据和远程数据](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)