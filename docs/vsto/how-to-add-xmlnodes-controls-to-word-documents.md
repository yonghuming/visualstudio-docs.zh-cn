---
title: "如何：向 Word 文档添加 XMLNodes 控件 | Microsoft Docs"
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
  - "控件 [Visual Studio 中的 Office 开发], 添加到文档"
  - "XMLNodes 控件, 添加到文档"
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：向 Word 文档添加 XMLNodes 控件
  **重要事项** 有关 Microsoft Word 的本主题开头的信息对于位于美国境外及其领土或使用对单个的优点和使用完全呈现和组织，或者运行的开发的程序，即在 2010 年一月之前的 Microsoft 许可证的 Microsoft Word 产品，那么，当 Microsoft 从 Microsoft Word 移除了特殊功能的实现与自定义 XML 相关。  凡位于美国及其各州内的个体或组织，在使用或开发用于在由 Microsoft 于 2010 年 1 月 10 日之后授予许可的 Microsoft Word 产品上运行的程序时，请勿参考或使用此与 Microsoft Word 相关的信息；这些产品与此许可日期之前的产品，或在美国以外的国家\/地区销售和授予使用许可的产品的行为不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 将重复 XML 架构元素映射到 Microsoft Office Word 文档时，Visual Studio 会自动将 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件添加到文档中。  
  
 有关映射非重复 XML 架构元素的信息，请参见[如何：向 Word 文档添加 XMLNode 控件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件不能从**“工具箱”**或**“数据源”**窗口中获取，也无法以编程方式创建。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 将 XMLNodes 控件添加到文档中  
  
1.  在 Visual Studio 设计器中的文档中，单击功能区上的**“开发人员”**选项卡。  
  
    > [!NOTE]  
    >  如果看不到**“开发人员”**选项卡，您必须首先显示该选项卡。  有关更多信息，请参见[如何：在功能区上显示“开发人员”选项卡](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
2.  在**“XML”**组中，单击**“架构”**。  
  
     **“模板和加载项”**对话框将打开。  
  
3.  单击**“XML 架构”**选项卡。  
  
4.  单击**“添加架构”**。  
  
     随即打开**“添加架构”**对话框。  
  
5.  选择包含重复架构元素的 XML 架构，然后单击**“打开”**。  
  
     随即出现**“架构设置”**对话框。  
  
6.  分配一个别名或单击**“确定”**，以添加没有别名的架构。  
  
     该架构被添加到**“添加架构”**对话框中。  
  
7.  在**“添加架构”**对话框中单击**“确定”**。  
  
     随即打开**“XML 结构”**任务窗格。  
  
8.  单击**“XML 结构”**任务窗格中的重复架构元素，以将其添加到文档中。  
  
     一个 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控件即被创建并添加到项目中。  
  
## 请参阅  
 [XMLNodes 控件](../vsto/xmlnodes-control.md)   
 [使用扩展对象实现 Word 自动化](../vsto/automating-word-by-using-extended-objects.md)   
 [宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)   
 [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  