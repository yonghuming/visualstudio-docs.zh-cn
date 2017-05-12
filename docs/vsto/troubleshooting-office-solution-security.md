---
title: "Office 解决方案安全性疑难解答"
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
helpviewer_keywords: 
  - "安全性 [Visual Studio 中的 Office 开发], 疑难解答"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Office 解决方案安全性疑难解答
  本主题包含一些提示，可用于解决在保护 Office 解决方案安全时可能会遇到的一些常见问题。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 无法从受限站点安装受信任解决方案  
 如果该网站将在 Internet Explorer 受限站点区域，列表用户无法安装从 web 位置的解决方案。  即使该解决方案已用受信任的证书签名，也是如此。  
  
 可以将部署清单的 URL 分类到五个区域之一：  
  
-   我的电脑  
  
-   Internet  
  
-   本地 Intranet  
  
-   受信任站点  
  
-   受限站点  
  
 如果已经将部署清单的位置分配给受限站点区域，则 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]不会安装解决方案。  如果该位置是已知的并且可以信任，则用户可以从受限站点区域中移除该位置，然后安装解决方案。  有关如何管理区域的信息，请参见 [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774)（配置 ClickOnce 受信任发布者）。  
  
## 在安装了 Internet Explorer 增强的安全配置或 Internet Explorer 7 的情况下，无法从网络文件共享或 Web 位置安装解决方案  
 Internet Explorer 增强了在 Windows Server 2003 的安全配置 \(IEESC\) 和更高，因此，Internet Explorer 7 和更高版本中，大限制用户浏览 Internet 的能力。  当用户尝试安装从网络文件共享或 web 位置 Office 解决方案时，他们会收到以下错误消息：，因为用于部署清单签名的证书为 *SolutionName* 不受信任，“此应用程序中的自定义的函数不起作用。  请与管理员联系，以获得进一步的帮助。”  
  
 IEESC 和 Internet Explorer 7 和更高，因此，如果部署清单的 URL 在 Internet 区域类别，清单必须具有来自受信任发行者的证书或不能安装解决方案。  未安装 IEESC 时，默认行为是提示最终用户做出信任决定。  
  
 若要控制 IEESC 和 Internet Explorer 7 的角色和更高版本中，请确定您信任并将它们添加到其中一个受信任的安全区域的网站和通用命名约定 \(UNC\) 路径 \("本地 Intranet "或"受信任站点\)。有关如何管理区域的信息，请参见 [配置 ClickOnce 受信任的发行者](http://go.microsoft.com/fwlink/?LinkId=94774)。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  