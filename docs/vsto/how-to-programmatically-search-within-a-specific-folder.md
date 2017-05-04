---
title: "如何：以编程方式在特定文件夹中搜索 | Microsoft Docs"
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
  - "Outlook 文件夹 [Visual Studio 中的 Office 开发], 搜索"
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：以编程方式在特定文件夹中搜索
  此代码示例使用 `Find` 和 `FindNext` 方法在**“收件箱”**中的电子邮件的主题字段中搜索文本。  此方法使用字符串筛选器检查字母 T 是否为 `Subject` 文本的开头字母。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_OL_SearchFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchFolder/CS/thisaddin.cs#1)]  
  
## 请参阅  
 [使用文件夹](../vsto/working-with-folders.md)   
 [Outlook 对象模型概述](../vsto/outlook-object-model-overview.md)   
 [如何：以编程方式按名称检索文件夹](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  