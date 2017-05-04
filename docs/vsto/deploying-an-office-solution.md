---
title: "部署 Office 解决方案 | Microsoft Docs"
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
  - "ClickOnce 部署 [Visual Studio 中的 Office 开发], 关于 ClickOnce 解决方案部署"
  - "ClickOnce 部署 [Visual Studio 中的 Office 开发], 事件查看器"
  - "ClickOnce 部署 [Visual Studio 中的 Office 开发], 疑难解答"
  - "部署应用程序 [Visual Studio 中的 Office 开发], 事件查看器"
  - "部署应用程序 [Visual Studio 中的 Office 开发], Office 解决方案 (2007 system)"
  - "部署应用程序 [Visual Studio 中的 Office 开发], 疑难解答"
  - "Office 应用程序 [Visual Studio 中的 Office 开发], 部署 Office 解决方案"
  - "Visual Studio 中的 Office 开发, 部署 Office 解决方案"
  - "Visual Studio 中的 Office 开发, 事件查看器"
  - "Visual Studio 中的 Office 开发, 疑难解答"
  - "Office 解决方案 [Visual Studio 中的 Office 开发], 部署"
  - "解决方案 [Visual Studio 中的 Office 开发], 部署 Office 解决方案 (2007 system)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# 部署 Office 解决方案
  可以使用 ClickOnce 或 Windows Installer 来部署 Office 解决方案。  通过使用 ClickOnce，可以减少部署和更新解决方案所需的步骤数。  如果使用 Windows Installer，可以控制解决方案的安装方式，以及在用户安装解决方案时，安装程序显示的页。  
  
## 使用 ClickOnce 部署解决方案  
 使用 ClickOnce 部署解决方案时，可将其发布到一个中心位置，用户能够从中安装并运行解决方案。  可以更新解决方案，而无需将新的安装程序分发给用户。此部署选项更简单，但无法显示用户自定义安装页。  此外，必须在包含多个用户的任何计算机上多次安装解决方案。  请参阅[使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## 使用 Windows Installer 部署解决方案  
 使用 Windows Installer 部署解决方案时，可将安装程序分发给用户，用户将使用此程序安装解决方案。  安装程序可以同时为一台计算机上的所有用户安装解决方案，而非仅当前用户。  还可以更好地控制在用户安装解决方案时显示给用户的选项。  例如，可以显示许可协议或者使用户安装解决方案的特定组件。  不过，如果更新解决方案，必须分发一个新的安装程序。  请参阅[使用 Windows Installer 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [使用 ClickOnce 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [使用 Windows Installer 部署 Office 解决方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Office 解决方案部署疑难解答](../vsto/troubleshooting-office-solution-deployment.md)  
  
  