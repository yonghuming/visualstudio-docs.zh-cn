---
title: "如何：自定义内置选项卡"
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
  - "内置选项卡 [Visual Studio 中的 Office 开发]"
  - "功能区 [Visual Studio 中的 Office 开发], 选项卡"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：自定义内置选项卡
  可以将组和控件添加到内置选项卡。  内置选项卡是已在 Microsoft Office 应用程序功能区的选项卡。  例如，**“数据”**选项卡是 Excel 中的内置选项卡。  创建自定义组时，它显示在选项卡末尾，但可以在选项卡上任意移动你的组。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  可以将组添加到内置选项卡，但不能删除内置选项卡中的内置组。  
  
### 将组添加到内置选项卡  
  
1.  右键单击**“解决方案资源管理器”**中的功能区代码文件，然后单击**“视图设计器”**。  
  
    > [!NOTE]  
    >  如果功能区代码文件未出现在**“解决方案资源管理器”**中，则必须将**“功能区项”**添加到项目中。  请参阅[如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  右键单击功能区设计器中的任何选项卡，然后单击**“属性”**。  
  
3.  在**“属性”**窗口中，展开 **ControlId** 属性，然后将 **ControlIdType** 属性设置为 **Office**。  
  
4.  将 **OfficeId** 属性设置为需要自定义的内置选项卡的*“控件 ID”*。  
  
     控件 ID 是唯一标识 Microsoft Office 应用程序中内置的选项卡、组和控件的名称。  
  
     有关控件 ID 的列表，请参阅 [Office 2010 帮助文件：Office Fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
5.  从**“工具箱”**的**“Office 功能区控件”**选项卡中，将组拖到选项卡。  
  
    > [!NOTE]  
    >  设计器中不显示内置组。  因此，确定自己是否正在使用内置选项卡的唯一方法是检查选项卡的 **ControlId** 属性。  
  
### 若要在内置选项卡上定位组  
  
1.  在“功能区设计器”中，选择自定义组。  
  
2.  在**“属性”**窗口中，展开 **Position** 属性。  
  
3.  将 **PositionType** 属性设置为适当值：  
  
    -   **BeforeOfficeId** 将定位所指定内置组之前的组。  
  
    -   **AfterOfficeId** 将定位所指定内置组之后的组。  
  
4.  将 **OfficeId** 属性设置为内置组的控件 ID。  
  
     有关控件 ID 的列表，请参阅 [Office 2010 帮助文件：Office Fluent 用户界面控件标识符](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## 请参阅  
 [功能区概述](../vsto/ribbon-overview.md)   
 [功能区设计器](../vsto/ribbon-designer.md)   
 [功能区 XML](../vsto/ribbon-xml.md)   
 [演练：使用功能区设计器创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [演练：使用功能区 XML 创建自定义选项卡](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [如何：开始自定义功能区](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何：更改功能区上选项卡的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何：向 Backstage 视图添加控件](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：显示外接程序用户界面错误](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  