---
title: "向“数据源”窗口添加自定义控件 | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据源窗口，添加控件"
  - "控件 [Visual Studio]，添加到“数据源”窗口"
  - "DefaultBindingPropertyAttribute 类，使用"
  - "LookupBindingPropertiesAttribute 类，使用"
  - "ComplexBindingPropertiesAttribute 类，使用"
  - "数据源窗口，选择控件"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向“数据源”窗口添加自定义控件
将项从**“数据源”**窗口拖到设计图面来创建数据绑定控件时，您可以选择所创建的控件的类型。  该窗口中的每一项都有一个下拉列表，该列表显示您可从中进行选择的控件。  与每一项关联的控件集由该项的数据类型确定。  如果要创建的控件未出现在列表中，您可以按照本主题中的说明进行操作，将该控件添加到列表中。  
  
 有关选择要为**“数据源”**窗口中的项创建的数据绑定控件的更多信息，请参见[设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
##  <a name="customizinglist"></a> 自定义数据类型的可绑定控件列表  
 执行以下步骤，以便为**“数据源”**窗口中具有特定数据类型的项向列表中添加控件，或从列表中移除控件。  
  
#### 选择要为某个数据类型列出的控件  
  
1.  确保 WPF 设计器或 Windows 窗体设计器已打开。  
  
2.  在**“数据源”**窗口中，单击作为添加到窗口的数据源的一部分的项，然后单击该项的下拉菜单。  
  
3.  在下拉菜单中，单击**“自定义”**。  以下对话框之一将打开：  
  
    -   如果 Windows 窗体设计器已打开，则**“选项”**对话框的**“自定义数据 UI”**页将打开。  
  
    -   如果 WPF 设计器已打开，则**“自定义控件绑定”**对话框将打开。  
  
4.  在该对话框中，从**“数据类型”**下拉列表中选择一个数据类型。  
  
    -   若要为表或对象自定义控件的列表，请选择 **“\[列表\]”**。  
  
    -   若要为表的列或对象的属性自定义控件的列表，请在基础数据存储中选择列或属性的数据类型。  
  
    -   若要自定义控件的列表以显示具有用户定义形状的数据对象，请选择 **“\[其他\]”**。  例如，如果应用程序具有从特定对象的多个属性显示数据的自定义控件，则选择**“\[其他\]”**。  
  
5.  在**“关联的控件”**框中，选择希望供选定数据类型使用的每个控件，或根据需要清除选择要从列表中移除的任何控件。  
  
    > [!NOTE]
    >  如果要选择的控件未出现在**“关联的控件”**框中，您必须将该控件添加到列表。  有关更多信息，请参见[将控件添加到数据类型的关联控件列表](#addingcontrols)。  
  
6.  单击**“确定”**。  
  
7.  在**“数据源”**窗口中，单击刚刚关联一个或多个控件的数据类型的项，然后单击该项的下拉菜单。  
  
     在**“关联的控件”**框中选择的控件现在将出现在该项的下拉菜单中。  
  
##  <a name="addingcontrols"></a> 将控件添加到数据类型的关联控件列表  
 如果要将某个控件与数据类型关联，但该控件未出现在**“关联的控件”**框中，则必须将该控件添加到列表。  控件必须位于当前解决方案或引用的程序集中，在**“工具箱”**中可用，并且具有指定控件的数据绑定行为的特性。  
  
#### 将控件添加到关联控件列表  
  
1.  右击**“工具箱”**并选择**“选择项”**，将所需控件添加到**“工具箱”**中。  
  
     控件必须具有以下特性之一。  
  
    |特性|说明|  
    |--------|--------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|在显示数据的单个列（或属性）的简单控件（如 <xref:System.Windows.Forms.TextBox>）上实现此特性。|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|在显示数据的列表（或表）的控件（如 <xref:System.Windows.Forms.DataGridView>）上实现此特性。|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|在既显示数据列表（或表）又需要显示单个列或属性的控件（如 <xref:System.Windows.Forms.ComboBox>）上实现此特性。|  
  
2.  打开**“选项”**对话框的**“自定义数据 UI”**页（对于 Windows 窗体），或打开**“自定义控件绑定”**对话框（对于 WPF）。  有关更多信息，请参见[自定义数据类型的可绑定控件列表](#customizinglist)。  
  
3.  在**“关联的控件”**框中，现在应显示您刚刚添加到**“工具箱”**的控件。  
  
    > [!NOTE]
    >  只有位于当前解决方案或引用的程序集中（并实现上表中的数据绑定特性之一）的控件才能添加到关联控件的列表。  若要将数据绑定到在**“数据源”**窗口中不可用的自定义控件，请从**“工具箱”**中将该控件拖动到设计图面上，然后将要绑定到的项从**“数据源”**窗口拖动到该控件上。  
  
## 请参阅  
 [演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [数据源概述](../data-tools/add-new-data-sources.md)   
 [设置从“数据源”窗口中拖动时要创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [演练：创建支持简单数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [演练：创建支持复杂数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [演练：创建支持查找数据绑定的 Windows 窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [“自定义控件绑定”对话框](../data-tools/customize-control-binding-dialog-box.md)