---
title: "如何：以编程方式在 Outlook 中移动项 | Microsoft Docs"
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
  - "Outlook 文件夹 [Visual Studio 中的 Office 开发], 移动项"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以编程方式在 Outlook 中移动项
  此示例将未阅读的电子邮件从**“收件箱”**移动到名为 **Test** 的文件夹中。  此示例仅移动在 `Subject` 字段中具有文字 **Test** 的电子邮件。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## 编译代码  
 此示例需要：  
  
-   取名为 **Test** 的 Outlook 邮件文件夹。  
  
-   在 `Subject` 字段中具有文字 **Test** 的电子邮件。  
  
## 请参阅  
 [使用文件夹](../vsto/working-with-folders.md)   
 [如何：以编程方式按名称检索文件夹](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以编程方式在特定文件夹中搜索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [如何：以编程方式在收到电子邮件后执行操作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  