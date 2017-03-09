---
title: "“自定义控件绑定”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "“自定义控件绑定”对话框"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# “自定义控件绑定”对话框
使用**“自定义控件绑定”**对话框可以指定适用于[“数据源”窗口](../Topic/Data%20Sources%20Window.md)中的各个项的控件。  
  
 **“数据源”**窗口中的每个项都有一个关联列表，其中列出了可绑定到该项的各个控件。  可供每项使用的控件取决于该项的数据类型。  每种数据类型都在此对话框中定义了有效关联控件的列表，包括默认控件。  
  
 在将某个项拖至设计图面上以创建数据绑定控件之前，您可以选择要创建的控件。  如果在没有选择控件的情况下将某个项从**“数据源”**窗口拖至设计图面上，则会将选定项的数据类型对应的默认控件添加到设计图面中。  
  
 有关如何使用此对话框为**“数据源”**窗口中的各个项自定义控件列表的更多信息，请参见[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
## UIElement 列表  
 **数据类型**  
 显示与控件关联的类型的列表：  
  
-   表、实体和对象表示为**“\[列表\]”**类型。  
  
-   列或实体和对象的公共属性表示为基础数据存储区中的列或属性的实际数据类型。  
  
-   具有用户定义的类型的对象表示为**“\[其他\]”**。  例如，如果应用程序具有从对象的多个属性显示数据的自定义控件，则为您的控件选择**“\[其他\]”**数据类型。  
  
 **关联控件**  
 显示可与特定数据类型关联的控件的列表。  如果要使特定控件与在**“数据类型”**列表中选择的数据类型相关联，请选中相应的复选框。  清除复选框可以移除关联。  选中的控件会出现在**“数据源”**窗口为关联数据类型的项显示的快捷菜单中。  
  
 可以通过将具有若干数据绑定特性之一的控件添加到**“工具箱”**中来向列表中添加控件。  有关更多信息，请参见[向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
 **设置默认值**  
 将选定的控件类型指定为所选数据类型的项的默认值。  默认控件将作为第一个选项出现在**“数据源”**窗口为某个项显示的快捷菜单中。  只能指定一种控件类型作为数据类型的默认控件。  
  
 **清除默认值**  
 取消将控件指定为选定数据类型的默认控件。  如果选定数据类型没有默认控件，则**“\[无\]”**将作为第一个选项出现在**“数据源”**窗口为关联类型的项显示的快捷菜单中。  
  
## 请参阅  
 [“数据源”窗口](../Topic/Data%20Sources%20Window.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [向“数据源”窗口添加自定义控件](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)