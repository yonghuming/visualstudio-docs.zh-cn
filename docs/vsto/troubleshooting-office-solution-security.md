---
title: "Office 解决方案安全性疑难解答 |Microsoft 文档"
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
helpviewer_keywords: security [Office development in Visual Studio], troubleshooting
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2bf7b639504d6bca53af590d200d9d291ddcd66b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-office-solution-security"></a>Office 解决方案安全性疑难解答
  本主题包含用于解决在保护 Office 解决方案时可能遇到的常见问题的提示。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>受信任的解决方案不能从受限制的站点中安装  
 如果在 Internet Explorer 受限的站点区域中列出的网站，用户不能从某一 web 位置安装解决方案。 即使解决方案使用受信任的证书进行签名，也是如此。  
  
 部署清单的 URL 可以分为五个区域之一：  
  
-   我的计算机  
  
-   Internet  
  
-   本地 intranet  
  
-   受信任的站点  
  
-   受限制的站点  
  
 如果向受限的站点区域中，分配了部署清单的位置[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]不会安装解决方案。 如果位置称为，它可以是受信任，则用户可以从受限制的站点区域中删除位置并安装解决方案。 有关如何管理区域的信息，请参阅[配置 ClickOnce 受信任的发行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer 增强的安全配置或安装 Internet Explorer 7 时，不能从网络文件共享或 Web 位置安装解决方案  
 Internet Explorer 增强安全配置 （安装 ieesc 时） 在 Windows Server 2003 和更高版本和 Internet Explorer 7 及更高版本，显著限制用户能够浏览 Internet。 当用户尝试从网络文件共享或 web 位置安装 Office 解决方案时，它们可能会收到以下错误消息:"由于使用的部署清单签名的证书，此应用程序中的自定义功能将无法工作*SolutionName*不受信任。 请联系您的管理员联系以获得进一步帮助。"  
  
 与安装 ieesc 时和 Internet Explorer 7 及更高版本，如果在 Internet 区域中，部署清单的 URL 进行分类，清单必须具有受信任的发布者的证书，或无法安装解决方案。 未安装 ieesc 时，默认行为是提示最终用户做出信任决定。  
  
 若要管理的效果安装 ieesc 时和 Internet Explorer 7 和更高版本，确定网站和通用命名约定 (UNC) 路径你信任并将它们添加到受信任的安全区域 （本地 intranet 或受信任的站点） 之一。有关如何管理区域的信息，请参阅[配置 ClickOnce 受信任的发行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## <a name="see-also"></a>另请参阅  
 [确保 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  