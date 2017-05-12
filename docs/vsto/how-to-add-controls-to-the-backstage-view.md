---
title: "如何：向 Backstage 视图添加控件"
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
  - "控件, 功能区"
  - "自定义功能区, 菜单"
  - "自定义功能区, 菜单"
  - "菜单, 自定义"
  - "Microsoft Office 按钮"
  - "Microsoft Office 菜单"
  - "Office 按钮"
  - "功能区, 自定义"
  - "功能区, 菜单"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：向 Backstage 视图添加控件
  可以使用功能区设计器将控件添加到打开的菜单中，单击时 **文件** 选项。  在运行应用程序时，已添加到 **文件** 选项的控件显示组名为 **外接程序**。  
  
 使用 Visual Studio 中，功能区设计器不能在内部控件之前或之后可以定位控件。  内置控件已经显示 backstage 视图的控件。  如果要将控件放在内置控件的前面或后面，则必须使用功能区 XML。  有关 **功能区 \(XML\)**的更多信息，请参见 [功能区 XML](../vsto/ribbon-xml.md)。  有关自定义 Backstage 视图的更多信息，请参见 [Introduction to the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182189)（Office 2010 Backstage 视图简介 \- 适用于开发人员）和  [Customizing the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188)（自定义 Office 2010 Backstage 视图 \- 适用于开发人员）。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 将控件添加到 backstage 视图  
  
1.  在“设计”视图中打开功能区项。  
  
     有关如何向项目添加**“功能区\(可视化设计器\)”**项的更多信息，请参见[如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在功能区设计器中，单击 **文件** 选项。  
  
     显示一个菜单设计器。  此设计图面不包含任何控件。  
  
3.  从**“工具箱”**的**“Office 功能区控件”**选项卡上，将以下任意控件拖到菜单设计器上：  
  
    -   Button  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   Menu  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  拖动控件，将其移至菜单上的新位置。  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  