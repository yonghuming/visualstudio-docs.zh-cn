---
title: "如何：对 Office 解决方案进行签名"
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
  - "证书 [Visual Studio 中的 Office 开发], Office 解决方案"
  - "安全性 [Visual Studio 中的 Office 开发], 对 Office 解决方案进行签名"
  - "对清单进行签名 [Visual Studio 中的 Office 开发]"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：对 Office 解决方案进行签名
  如果为解决方案签名，您可以使用证书作为证据向解决方案授予信任。  您可以为多个解决方案使用同一证书，并且无需额外更新安全策略即可使所有解决方案得到信任。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果使用清单生成和编辑工具（mage.exe 和 mageui.exe）手动编辑应用程序清单和部署清单，您必须对这些清单进行重新签名，然后才能使用它们。  有关更多信息，请参见[如何：为应用程序和部署清单重新签名](~/deployment/how-to-re-sign-application-and-deployment-manifests.md)。  
  
## 使用证书进行签名  
 证书是一个文件，其中包含解决方案发布者的唯一密钥和标识。  您可以从证书颁发机构购买证书，也可以创建自己的证书并让证书颁发机构为其签名。  
  
 为启用调试，Visual Studio 会使用一个临时证书对 Office 解决方案进行签名。  您不应将已部署解决方案中的临时证书用作证据。  
  
#### 使用证书为 Office 解决方案签名  
  
1.  在**“项目”**菜单上，单击“*解决方案名称* **属性”**。  
  
2.  单击**“签名”**选项卡。  
  
3.  选择**“为 ClickOnce 清单签名”**。  
  
4.  通过单击**“从存储区选择”**或**“从文件选择”**并定位到证书来查找证书。  
  
5.  若要验证是否在使用正确的证书，请单击**“更多详细信息”**来查看证书信息。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [向 Office 解决方案授予信任](../vsto/granting-trust-to-office-solutions.md)   
 [“项目设计器”-&#62;“签名”页](../ide/reference/signing-page-project-designer.md)  
  
  