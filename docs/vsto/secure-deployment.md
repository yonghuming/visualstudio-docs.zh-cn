---
title: "安全部署 | Microsoft Docs"
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
  - "ClickOnce 部署 [Visual Studio 中的 Office 开发], 安全性"
  - "部署应用程序 [Visual Studio 中的 Office 开发], 安全性"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 安全性"
  - "Visual Studio 中的 Office 开发, 安全性"
ms.assetid: c5ba86b1-e87f-4508-8c5a-1295681a9590
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# 安全部署
  在创建 Office 解决方案时，将自动更新开发计算机以允许运行项目中的代码。  但在部署解决方案时，必须通过使用证书对解决方案进行签名或使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 信任提示密钥，从而提供信任决定所基于的证据。  有关更多信息，请参见[向 Office 解决方案授予信任](../vsto/granting-trust-to-office-solutions.md)。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 对于文档级自定义项，如果将文档部署到网络位置，还必须在该 Office 应用程序的信任中心将文档的位置添加到受信位置列表中。  有关如何在最终用户计算机上设置文档权限的更多信息，请参见[向文档授予信任](../vsto/granting-trust-to-documents.md)。  
  
## 防止 Office 解决方案运行代码  
 管理员可以使用注册表来防止所有 Office 解决方案在计算机上运行。  当托管代码扩展时打开的 Office 解决方案，Visual Studio for Office 运行时检查工具使用名称 `Disabled` 的项是否存在计算机上的以下注册表项之一以下操作：  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 若要防止 Office 解决方案运行代码，请在其中一个或全部两个注册表项下创建 `Disabled` 项，并为 `Disabled` 指定以下数据类型和值之一：  
  
-   设置为“0”（零）之外的任何字符串的 REG\_SZ 或 REG\_EXPAND\_SZ。  
  
-   设置为 0（零）之外的任何值的 REG\_DWORD。  
  
 若要使 Office 解决方案能够运行代码，请将两个 `Disabled` 项均设置为 0（零），或者删除这两个注册表项。  
  
## 请参阅  
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [准备计算机以运行或承载 Office 解决方案](http://msdn.microsoft.com/zh-cn/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  