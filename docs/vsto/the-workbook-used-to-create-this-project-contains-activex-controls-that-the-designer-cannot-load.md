---
title: "用于创建此项目的工作簿包含设计器无法加载的 ActiveX 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.SelectDocWizard.ContainsActiveXControls"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# 用于创建此项目的工作簿包含设计器无法加载的 ActiveX 控件
  以编程方式向 Word 文档或 Excel 工作表添加控件时出现此错误，请保存文档或工作簿，然后基于文档或工作簿创建新的文档级解决方案。  
  
 介绍控件托管类型的信息不会随文档或工作簿一起保存。  基于该文档或工作簿创建新的解决方案时，Visual Studio 没有足够的信息来加载主机项设计器中的控件。  
  
### 更正此错误  
  
1.  打开文档或工作簿。  
  
2.  删除在运行时添加的控件。  可通过在文档或工作簿中选择这些控件并按 Delete 键来完成此操作。  
  
3.  基于文档或工作簿创建文档级解决方案。  
  
## 请参阅  
 [如何：在 Visual Studio 中创建 Office 项目](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [在运行时向 Office 文档添加控件](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  