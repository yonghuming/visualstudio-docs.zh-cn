---
title: "如何：向功能区组添加对话框启动器 | Microsoft Docs"
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
  - "对话框启动器 [Visual Studio 中的 Office 开发]"
  - "功能区 [Visual Studio 中的 Office 开发], 对话框启动程序"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何：向功能区组添加对话框启动器
  可以向功能区上的任何组添加对话框启动器。  对话框启动器是在组中显示的一个小图标。  用户单击此图标可以打开相关对话框或任务窗格，其中提供更多与该组相关的选项。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 向功能区组添加对话框启动器  
  
1.  在**“解决方案资源管理器”**中，选择功能区代码文件（.vb 或 .cs 文件）。  
  
2.  在**“视图”**菜单上，单击**“设计器”**。  
  
3.  在功能区设计器中，右击任何一个组，然后单击**“添加 DialogBoxLauncher”**。  
  
     向该组的 <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> 事件添加代码以打开自定义或内置对话框。  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [在运行时访问功能区](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 开发示例和演练](../vsto/office-development-samples-and-walkthroughs.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区对象模型概述](../vsto/ribbon-object-model-overview.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [如何：将功能区从功能区设计器导出为功能区 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：更改功能区上选项卡的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何：自定义内置选项卡](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：向 Backstage 视图添加控件](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [自定义 Outlook 功能区](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何：显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：在运行时更新功能区上的控件](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  