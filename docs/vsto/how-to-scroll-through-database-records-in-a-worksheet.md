---
title: "如何：在工作表中滚动查看数据库记录 | Microsoft Docs"
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
  - "数据 [Visual Studio 中的 Office 开发], 滚动数据库记录"
  - "数据库 [Visual Studio 中的 Office 开发], 滚动记录"
  - "记录 [Visual Studio 中的 Office 开发], 滚动"
  - "工作表 [Visual Studio 中的 Office 开发], 滚动记录"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：在工作表中滚动查看数据库记录
  下面的过程演示如何使用设计器，通过允许最终用户滚动查看所有记录的控件，在 Microsoft Office Excel 工作表中显示数据库表中的单个字段。  
  
 仅能在文档级项目中使用设计器。  但是，您也可以添加控件并在运行时以编程方式将它们绑定到数据。  有关更多信息，请参见[演练：VSTO 外接程序项目中的简单数据绑定](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### 在工作表中滚动查看数据库记录  
  
1.  在 Visual Studio 中打开一个 Excel 应用程序项目。  
  
2.  打开**“数据源”**窗口，并从数据库创建一个数据源。  有关更多信息，请参见[如何：连接到数据库中的数据](~/data-tools/how-to-connect-to-data-in-a-database.md)。  
  
3.  展开包含要显示数据的表，并选择特定的列。  
  
4.  打开控件列表，并选择**“NamedRange”**。  
  
5.  将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件拖动到要显示数据的单元格上。  
  
6.  从**“工具箱”**的**“Windows 窗体”**选项卡中向工作表添加一个 <xref:System.Windows.Forms.BindingNavigator> 控件，并设置要使用的控件。  有关更多信息，请参见[BindingNavigator 控件概述（Windows 窗体）](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)。  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  