---
title: "如何：以编程方式及工作簿形式打开文本文件 | Microsoft Docs"
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
  - "文本 [Visual Studio 中的 Office 开发], 文本文件"
  - "文本文件, 以工作簿形式打开"
  - "工作簿, 将文本文件打开为"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 如何：以编程方式及工作簿形式打开文本文件
  可以将文本文件作为工作簿打开。  必须传入要打开的文本文件的名称。  可以指定一些可选参数，例如，要从哪一行开始分析以及文件中数据的列格式。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 示例  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## 编译代码  
 此示例需要以下组件：  
  
-   一个名为 `Test.txt` 的逗号分隔的文本文件，其中至少包含三行文本。  
  
-   要存储在驱动器 C 上的文本文件 `Test.txt`。  
  
## 请参阅  
 [使用工作簿](../vsto/working-with-workbooks.md)   
 [如何：以编程方式打开工作簿](../vsto/how-to-programmatically-open-workbooks.md)   
 [如何：以编程方式新建工作簿](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [如何：以编程方式保存工作簿](../vsto/how-to-programmatically-save-workbooks.md)   
 [如何：以编程方式关闭工作簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)  
  
  