---
title: "如何：以编程方式确定当前的 Outlook 项"
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
  - "电子邮件 [Visual Studio 中的 Office 开发], 当前项"
  - "邮件项 [Visual Studio 中的 Office 开发], 当前"
  - "Outlook [Visual Studio 中的 Office 开发], 当前项"
  - "SelectionChange 事件"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：以编程方式确定当前的 Outlook 项
  此示例使用 Explorer.SelectionChange 事件显示当前文件夹的名称以及有关选定项的某些信息。  代码随后将显示选定项。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## 编译代码  
 此示例需要：  
  
-   Microsoft Office Outlook 中的约会、联系人和电子邮件项。  
  
## 请参阅  
 [Outlook 对象模型概述](../vsto/outlook-object-model-overview.md)   
 [如何：以编程方式按名称检索文件夹](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以编程方式搜索特定联系人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  