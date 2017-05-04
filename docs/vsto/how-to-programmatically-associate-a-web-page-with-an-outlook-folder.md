---
title: "如何：以编程方式将网页与 Outlook 文件夹关联 | Microsoft Docs"
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
  - "文件夹 [Visual Studio 中的 Office 开发], 网页"
  - "Outlook [Visual Studio 中的 Office 开发], 将网页附加到文件夹"
  - "网页 [Visual Studio 中的 Office 开发], Outlook 文件夹"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：以编程方式将网页与 Outlook 文件夹关联
  此示例检查 Microsoft Office Outlook 中是否存在名为 `HtmlView` 的文件夹。  如果文件夹不存在，代码将创建该文件夹并为其分配一个网页。  如果文件夹存在，代码将显示文件夹内容。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## 请参阅  
 [使用文件夹](../vsto/working-with-folders.md)   
 [如何：以编程方式按名称检索文件夹](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以编程方式创建自定义文件夹项](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  