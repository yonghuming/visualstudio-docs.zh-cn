---
title: "属性窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性 [Visual Studio]，属性窗口"
  - "处理程序函数，属性窗口"
  - "处理，“属性”窗口"
  - "Windows 消息"
  - "属性 [Visual Studio]，在设计时设置"
  - "属性 [Visual Studio]，编辑"
  - "属性浏览器"
  - "Windows 消息，添加消息处理程序"
  - "属性窗口，重写"
  - "虚函数，“属性”窗口"
  - "“属性”窗口"
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 属性窗口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用该窗口查看和更改位于编辑器和设计器中的选定对象的设计时属性及事件。  也可以使用**“属性”**窗口编辑和查看文件、项目和解决方案的属性。  可在“视图”菜单上找到“属性”窗口。  您还可以按 F4 或在“快速启动”窗口中键入属性来打开它。  
  
 **“属性”**窗口显示编辑字段的不同类型，具体取决于特定属性的需要。  这些编辑字段包括编辑框、下拉列表以及到自定义编辑器对话框的链接。  属性以灰色显示且是只读的。  
  
## UIElement 列表  
 对象名  
 列出当前选定的一个或多个对象。  只有活动编辑器或设计器中的对象可见。  当选择多个对象时，只出现所有选定对象的通用属性。  
  
 按分类顺序  
 按类别列出选定对象的所有属性及属性值。  可以折叠类别以减少可见属性数。  展开或折叠类别时，可以在类别名左边看到加号 \(\+\) 或减号 \(\-\)。  类别按字母顺序列出。  
  
 按字母顺序  
 按字母顺序对选定对象的所有设计时属性和事件排序。  若要编辑可用的属性，请在它右边的单元格中单击并输入更改内容。  
  
 属性页  
 显示选定项的**“属性页”**对话框或**“项目设计器”**。  “属性页”显示**“属性”**窗口中可用属性的子集、同一集合或超集。  使用该按钮可查看和编辑与项目的活动配置相关的属性。  
  
 属性  
 显示对象的属性。  很多对象的事件也可以使用**“属性”**窗口来查看。  
  
 按属性源排序  
 按源对属性分组，如继承、应用的样式，以及绑定。  仅当在设计器中编辑 XAML 文件时可用。  
  
 事件  
 显示对象的事件。  
  
> [!NOTE]
>  仅当 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 项目上下文中的窗体或控件设计器处于活动状态时，此**“属性”**窗口工具栏控件才可用。  在编辑 XAML 文件时，事件将出现在一个单独的属性窗口选项卡上。  
  
 Messages  
 列出所有 Windows 消息。  为选定类的消息添加或删除指定处理函数。  
  
> [!NOTE]
>  仅当**“类视图”**在 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目的上下文中为活动窗口时，此**“属性”**窗口工具栏控件才可用。  
  
 Overrides  
 列出选定类的所有虚函数并允许您添加或删除重写函数。  
  
> [!NOTE]
>  仅当**“类视图”**在 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 项目的上下文中为活动窗口时，此**“属性”**窗口工具栏控件才可用。  
  
 “说明”窗格  
 显示属性的属性类型和简短说明。  可以使用快捷菜单上的“说明”命令关闭和打开属性的说明。  
  
> [!NOTE]
>  在设计器中编辑 XAML 文件时，不可使用**“属性”**窗口工具栏控件。  
  
 缩略图视图  
 在设计器中编辑 XAML 文件时，显示了当前所选元素的可视表示形式。  
  
 搜索  
 在设计器中编辑 XAML 文件时，提供属性和事件的搜索功能。  搜索框对应于部分单词搜索并在您键入时候更新搜索结果。  
  
## 请参阅  
 [项目属性引用](../../ide/reference/project-properties-reference.md)   
 [自定义窗口布局](../../ide/customizing-window-layouts-in-visual-studio.md)