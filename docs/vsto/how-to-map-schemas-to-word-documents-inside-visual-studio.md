---
title: "如何：将架构映射到 Visual Studio 内部的 Word 文档"
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
  - "映射 [Visual Studio 中的 Office 开发], XML 架构到 Word 文档"
  - "Word [Visual Studio 中的 Office 开发], 映射 XML 架构"
  - "XML 架构 [Visual Studio 中的 Office 开发], 映射"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：将架构映射到 Visual Studio 内部的 Word 文档
  **重要事项** 有关 Microsoft Word 的本主题开头的信息对于位于美国境外及其领土或使用对单个的优点和使用完全呈现和组织，或者运行的开发的程序，即在 2010 年一月之前的 Microsoft 许可证的 Microsoft Word 产品，那么，当 Microsoft 从 Microsoft Word 移除了特殊功能的实现与自定义 XML 相关。  凡位于美国及其各州内的个体或组织，在使用或开发用于在由 Microsoft 于 2010 年 1 月 10 日之后授予许可的 Microsoft Word 产品上运行的程序时，请勿参考或使用此与 Microsoft Word 相关的信息；这些产品与此许可日期之前的产品，或在美国以外的国家\/地区销售和授予使用许可的产品的行为不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 当文档在 Visual Studio 中打开时，可以将 XML 架构映射到该文档。  使用的 Microsoft Office Word 工具与文档在 Visual Studio 外部打开时使用的工具相同。  不管是在创建 Word 解决方案之前还是之后将架构映射到文档，Office 项目都会创建相同的对象。  
  
### 在 Visual Studio 中将 XML 架构映射到 Word 文档  
  
1.  在 Visual Studio 内打开 Word 文档或模板项目。  
  
2.  在文档内部单击，使设计器获得焦点。  
  
3.  在功能区上，单击**“开发人员”**选项卡。  
  
    > [!NOTE]  
    >  如果看不到**“开发人员”**选项卡，您必须首先显示该选项卡。  有关更多信息，请参见[如何：在功能区上显示“开发人员”选项卡](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
4.  在**“XML”**组中，单击**“架构”**。  
  
     **“模板和加载项”**对话框将打开。  
  
5.  单击**“XML 架构”**选项卡。  
  
6.  单击**“添加架构”**。  
  
     随即打开**“添加架构”**对话框。  
  
7.  浏览至架构文件，选择该文件，然后单击**“打开”**。  
  
     **“架构设置”**对话框打开。  
  
8.  分配一个别名或单击**“确定”**，以添加没有别名的架构。  
  
9. 单击**“确定”**。  
  
     **“XML 结构”**窗口打开。  
  
10. 将元素从**“XML 结构”**窗口拖动到文档中要创建相应控件的位置。  
  
## 请参阅  
 [如何：将架构映射到 Visual Studio 内部的工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [文档级自定义项中的 XML 架构和数据](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  