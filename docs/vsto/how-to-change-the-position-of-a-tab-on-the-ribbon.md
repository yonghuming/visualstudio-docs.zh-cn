---
title: "如何：更改功能区上选项卡的位置"
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
  - "功能区 [Visual Studio 中的 Office 开发], 选项卡"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：更改功能区上选项卡的位置
  可以使用**“Tab 集合编辑器”**来更改功能区上自定义选项卡的顺序。  可以将自定义选项卡放置在功能区上内置选项卡的前面或后面。  内置选项卡是 Microsoft Office 应用程序的功能区上已存在的选项卡。  例如，**“数据”**选项卡是 Excel 中的内置选项卡。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 更改功能区上的选项卡的顺序  
  
1.  在**“解决方案资源管理器”**中，选择功能区代码文件（.vb 或 .cs 文件）。  
  
2.  在**“视图”**菜单上，单击**“设计器”**。  
  
3.  右击功能区设计器，然后单击**“属性”**。  
  
4.  在**“属性”**窗口中，选择**“Tab”**属性，然后单击省略号按钮 \(![ASP.NET 移动设计器中的省略号](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET 移动设计器中的省略号")\)。  
  
     将显示**“Tab 集合编辑器”**。  
  
5.  在**“Tab 集合编辑器”**的**“成员”**列表中，选择要移动的选项卡，然后单击向上或向下箭头来更改选项卡顺序。  
  
### 将选项卡放置在功能区上内置选项卡的前面或后面  
  
1.  在功能区设计器中，选择一个自定义选项卡。  
  
2.  在 **属性** 窗口中，展开 **ControlId** 属性，然后确保 **ControlIdType** 属性的值设置为 **自定义**。  
  
3.  在**“属性”**窗口中，展开**“Position”**属性。  
  
4.  将**“PositionType”**属性设置为适当的值：  
  
    -   **“BeforeOfficeId”**将组放置在指定内置选项卡的前面。  
  
    -   **“AfterOfficeId”**将组放置在指定内置选项卡的后面。  
  
5.  将**“OfficeId”**属性设置为内置选项卡的控件 ID。  
  
     有关控件 ID 的列表，请参见 [Office 2010 帮助文件：Office fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  