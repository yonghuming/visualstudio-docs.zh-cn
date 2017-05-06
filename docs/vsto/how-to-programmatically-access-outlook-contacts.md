---
title: "如何：以编程方式访问 Outlook 联系人"
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
  - "联系人 [Visual Studio 中的 Office 开发], 搜索"
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：以编程方式访问 Outlook 联系人
  此示例查找姓氏包含指定搜索字符串的所有联系人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/backup/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/VB/thisaddin.vb#1)]  
  
## 编译代码  
 此示例需要：  
  
-   在**“联系人”**文件夹中，姓氏包含字符串“**Na**”（例如，Tzipi Butnaru）的联系人。  
  
## 请参阅  
 [使用联系人项](../vsto/working-with-contact-items.md)   
 [如何：以编程方式向 Outlook 联系人添加项](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [如何：以编程方式搜索特定联系人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [如何：以编程方式在联系人中搜索电子邮件地址](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [如何：以编程方式删除 Outlook 联系人](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  