---
title: "如何：将功能区从功能区设计器导出为功能区 XML"
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
  - "自定义功能区, XML"
  - "自定义功能区, XML"
  - "导出功能区"
  - "功能区 [Visual Studio 中的 Office 开发], 导出"
  - "功能区 [Visual Studio 中的 Office 开发], XML"
  - "功能区设计器 [Visual Studio 中的 Office 开发]"
  - "XML [Visual Studio 中的 Office 开发], 功能区"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 如何：将功能区从功能区设计器导出为功能区 XML
  **“功能区\(可视化设计器\)”**项不支持功能区自定义项所有可能的类型。  若要以高级方式自定义功能区，可从设计器中将功能区导出为功能区 XML，然后直接编辑 XML。  
  
> [!NOTE]  
>  并非所有属性值都出现在功能区 XML 文件中。  有关更多信息，请参见[功能区概述](../vsto/ribbon-overview.md)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 将功能区从功能区设计器导出为功能区 XML  
  
1.  在**“解决方案资源管理器”**中右击功能区代码文件，然后单击**“视图设计器”**。  
  
2.  右击功能区设计器，然后单击**“将功能区导出到 XML”**。  
  
     Visual Studio 会向项目中添加一个功能区 XML 文件和一个功能区 XML 代码文件。  
  
3.  在功能区代码类中，找到以 `TODO:.` 开头的注释。  
  
4.  根据正在开发的解决方案的类型，将这些注释中的代码块复制到**“ThisAddin”**、**“ThisWorkbook”**或**“ThisDocument”**类中。  
  
     通过这些代码，Microsoft Office 应用程序能发现并加载自定义功能区。  有关更多信息，请参见[功能区 XML](../vsto/ribbon-xml.md)。  
  
5.  在**“ThisAddin”**、**“ThisWorkbook”**或**“ThisDocument”**类中，取消代码块的注释。  
  
     在取消注释代码后，您的代码应如下面的示例所示。  本例中，功能区类的名称为 `MyRibbon`。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  切换到功能区 XML 代码文件，然后找到 `Ribbon Callbacks` 区域。  
  
     这里就是编写回调方法以处理用户操作（如单击按钮）的位置。  
  
7.  为在功能区设计器代码中编写的每一个事件处理程序创建一个对应的回调方法。  
  
8.  将所有事件处理程序代码从事件处理程序中移至回调方法，然后修改这些代码以使用可扩展功能区 \(RibbonX\) 编程模型。  
  
     有关编写回调方法和使用 RibbonX 编程模型的信息，请参见[功能区 XML](../vsto/ribbon-xml.md)。  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  