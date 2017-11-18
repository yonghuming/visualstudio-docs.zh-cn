---
title: "在 Windows 窗体应用程序中创建查找表 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 00686648576ecc0f8054fe56112c5c47bb54adb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>在 Windows 窗体应用程序中创建查找表
术语*查找表*描述绑定到两个相关的数据表的控件。 这些查找控件显示基于在第二个表中选择的值的第一个表中的数据。  
  
 你可以通过将父表的主节点创建查找表 (从[数据源窗口](add-new-data-sources.md)) 拖到窗体已绑定到相关的子表中的列上的控件。  
  
 例如，假设有一个表的`Orders`销售数据库中。 在每个记录`Orders`表包括`CustomerID`，，该值指示下订单的哪些客户。 `CustomerID`是指向中的客户记录的外键`Customers`表。 在此方案中，你展开`Orders`表中**数据源**窗口并将主节点设置为**详细信息**。 然后设置`CustomerID`要使用列<xref:System.Windows.Forms.ComboBox>（或任何其他支持查找绑定的控件），并将其拖`Orders`拖动到窗体的节点。 最后，拖动`Customers`节点拖到控件绑定到相关列-在这种情况下，<xref:System.Windows.Forms.ComboBox>绑定到`CustomerID`列。  
  
## <a name="to-databind-a-lookup-control"></a>数据绑定的查找控件  
  
1.  打开**数据源**窗口。  
  
    > [!NOTE]
    >  查找表需要两个相关的表或对象是否位于**数据源**窗口。 有关详细信息，请参阅[数据集中的关系](relationships-in-datasets.md)。  
  
2.  展开中的节点**数据源**窗口，直到你可以看到父表和列，以及相关的子表的所有和所有其列。  
  
    > [!NOTE]
    >  子表节点是显示为父表中的可展开的子节点的节点。  
  
3.  更改到子表的拖放类型**详细信息**通过选择**详细信息**从子表节点上的控件列表。 有关详细信息，请参阅[设置从数据源窗口拖动时创建的控件](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)。  
  
4.  查找两个表相关的节点 (`CustomerID`上一示例中的节点)。到其拖放类型更改<xref:System.Windows.Forms.ComboBox>通过选择**ComboBox**从控件列表。  
  
5.  将从主要子表节点拖**数据源**拖动到窗体的窗口。  
  
     （带有描述性标签） 的数据绑定控件和一个工具条 (<xref:System.Windows.Forms.BindingNavigator>) 显示在窗体。 A[数据集](../data-tools/dataset-tools-in-visual-studio.md)， [TableAdapter](../data-tools/create-and-configure-tableadapters.md)， <xref:System.Windows.Forms.BindingSource>，和<xref:System.Windows.Forms.BindingNavigator>组件栏中出现。  
  
6.  现在将从主要父表节点**数据源**窗口直接拖到查找控件 ( <xref:System.Windows.Forms.ComboBox>)。  
  
     现在建立查找绑定。 请参阅下表中的设置在控件的特定属性。  
  
    |属性|设置说明|  
    |--------------|----------------------------|  
    |**数据源**|Visual Studio 将此属性设置为你拖到控件上的表所创建的 <xref:System.Windows.Forms.BindingSource>（相对于创建该控件时所创建的 <xref:System.Windows.Forms.BindingSource>）。<br /><br /> 如果你需要进行调整，则设置此为<xref:System.Windows.Forms.BindingSource>与你想要显示的列的表。|  
    |**DisplayMember**|对于你拖动到控件上的表，则 Visual Studio 将此属性设置为该主键后的具有字符串数据类型的第一列。<br /><br /> 如果你需要进行调整，然后将此设置为你想要显示的列名称。|  
    |**ValueMember**|Visual Studio 将此属性设置为参与主键的第一列，或表中的第一列（如果未定义任何键）。<br /><br /> 如果你需要进行调整，然后将此设置为具有你想要显示的列的表中的主键。|  
    |**SelectedValue**|Visual Studio 将此属性设置为从删除的原始列**数据源**窗口。<br /><br /> 如果你需要进行调整，然后将此设置为相关表中的外键列。|  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将 Windows 窗体控件绑定到数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)