---
title: "将自定义控件添加到数据源窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: d1efd7051d9119c4d0e6643c1d42e78d9cdde7cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>向“数据源”窗口添加自定义控件
中的项的拖时**数据源**到设计图面可创建数据绑定控件的窗口中，你可以选择你创建的控件的类型。 窗口中的每个项，有一个显示你可以从选择的控件的下拉列表。 通过项的数据类型确定与每个项关联的控件集。 如果你想要创建该控件不出现在列表中，你可以按照本主题中的说明将控件添加到列表。  
  
 选择数据绑定控件可以创建中的项目。 有关详细信息**数据源**窗口中，请参阅[设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你的当前设置或版本。 若要更改你的设置，在**工具**菜单上，选择**导入和导出设置**。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
##  <a name="customizinglist"></a>自定义数据类型可绑定控件的列表  
 若要添加或从可用控件中的项的列表中删除控件**数据源**窗口具有特定的数据类型，请执行以下步骤。  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>若要选择要为数据类型列出的控件  
  
1.  请确保 WPF 设计器或 Windows 窗体设计器处于打开状态。  
  
2.  在**数据源**窗口中，单击添加到窗口中，数据源中的项，然后单击项的下拉列表菜单。  
  
3.  在下拉列表菜单中，单击**自定义**。 将打开下列对话框之一：  
  
    -   Windows 窗体设计器处于打开状态，如果**数据 UI 自定义**页**选项**对话框随即打开。  
  
    -   如果 WPF 设计器处于打开状态，**自定义控件绑定**对话框随即打开。  
  
4.  在对话框中，选择数据类型从**数据类型**下拉列表。  
  
    -   若要自定义的表或对象的控件列表，请选择**[列表]**。  
  
    -   要自定义为一列的表或对象的属性的控件的列表，请在基础数据存储区中选择的列或属性的数据类型。  
  
    -   若要自定义控件以显示具有用户定义的形状的数据对象的列表，请选择**[其他]**。 例如，选择**[其他]**如果应用程序的特定对象的多个属性中显示的数据的自定义控件。  
  
5.  在**关联控件**框中，选择你想要用于所选的数据类型，每个控件或清除所选的任何你想要从列表中删除的控件。  
  
    > [!NOTE]
    >  如果你想要选择的控件中没有**关联控件**框中，你必须将控件添加到列表。 有关详细信息，请参阅[将控件添加到数据类型的关联控件列表](#addingcontrols)。  
  
6.  单击“确定”。  
  
7.  在**数据源**窗口中，单击数据的项键入您刚刚关联一个或多个控件，然后单击该项目的下拉列表菜单。  
  
     在中选择的控件**关联控件**框现在显示在下拉列表菜单项。  
  
##  <a name="addingcontrols"></a>将控件添加到数据类型的关联控件的列表  
 如果你想要将某个控件与数据类型，但控件未出现在**关联控件**框中，你必须将控件添加到列表。 该控件必须位于当前解决方案中，也可以引用的程序集中。 它还必须位于**工具箱**，并且具有一个属性，指定控件的数据绑定行为。  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>将控件添加到关联的控件的列表  
  
1.  添加到所需的控件**工具箱**通过右键单击**工具箱**并选择**选择项**。  
  
     控件必须具有以下属性之一。  
  
    |特性|描述|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|此属性显示的数据，单个列 （或属性） 的简单控件上实现如<xref:System.Windows.Forms.TextBox>。|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|实现显示数据列表 （或表） 的控件中此特性，如<xref:System.Windows.Forms.DataGridView>。|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|此属性显示的数据，但也需要显示的单个列或属性，列表 （或表） 的控件上实现如<xref:System.Windows.Forms.ComboBox>。|  
  
2.  Windows 窗体上**选项**对话框中，打开**数据 UI 自定义**页。 或者，对于 WPF 中，打开**自定义控件绑定**对话框。 有关详细信息，请参阅[自定义数据类型的可绑定控件列表的](#customizinglist)。  
  
3.  在**关联控件**框中，你只需添加到该控件**工具箱**现在应显示。  
  
    > [!NOTE]
    >  只有是位于当前解决方案中引用的程序集中的控件可以添加到关联的控件的列表。 （控件还必须实现数据绑定特性之一上表中。）若要将数据绑定到在中不可用的自定义控件**数据源**窗口中，将从该控件拖动**工具箱**拖到设计图面上，然后拖动要将绑定到中的项**数据源**窗口拖动到控件。  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)