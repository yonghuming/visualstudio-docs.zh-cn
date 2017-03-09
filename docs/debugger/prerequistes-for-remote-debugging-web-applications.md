---
title: "远程调试 Web 应用程序的必备组件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试 ASP.NET Web 应用程序, 远程服务器"
  - "远程调试, 系统必备"
  - "远程服务器, 调试 Web 应用程序"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 远程调试 Web 应用程序的必备组件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器，您可以在本地计算机或远程服务器上以透明方式调试 Web 应用程序。  这意味着，调试器始终以相同的方式运行，因而允许您在任一计算机上使用相同的功能。  但若要使远程调试正常进行，有一些先决条件。  
  
-   必须在要调试的服务器上安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 远程调试组件。  有关详细信息，请参阅[设置远程调试](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
-   默认情况下，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程作为 ASPNET 用户进程运行。  因此，您必须在运行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 的计算机上拥有管理员特权，才能对其进行调试。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 辅助进程的名称因调试方案和 IIS 版本而异。  有关详细信息，请参阅[如何：查找 ASP.NET 进程的名称](../debugger/how-to-find-the-name-of-the-aspnet-process.md)。  
  
## 请参阅  
 [调试 ASP.NET 和 AJAX 应用程序](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [系统要求](../debugger/aspnet-debugging-system-requirements.md)