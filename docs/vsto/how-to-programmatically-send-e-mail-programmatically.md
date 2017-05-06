---
title: "如何：以编程方式发送电子邮件"
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
  - "电子邮件 [Visual Studio 中的 Office 开发], 发送"
  - "邮件项 [Visual Studio 中的 Office 开发], 发送电子邮件"
  - "Outlook [Visual Studio 中的 Office 开发], 创建电子邮件"
  - "Outlook [Visual Studio 中的 Office 开发], 发送电子邮件"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以编程方式发送电子邮件
  此示例将电子邮件发送到电子邮件地址中具有域名 **example.com** 的联系人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## 编译代码  
 此示例需要：  
  
-   电子邮件地址中具有域名 **example.com** 的联系人。  
  
## 可靠编程  
 不要移除搜索域名 **example.com** 的筛选器代码。  如果移除此筛选器，解决方案会向您的所有联系人发送电子邮件。  
  
## 请参阅  
 [使用邮件项](../vsto/working-with-mail-items.md)   
 [如何：以编程方式创建电子邮件项](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [如何：以编程方式访问 Outlook 联系人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以编程方式在收到电子邮件后执行操作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  