---
title: "设置从数据源窗口拖动时创建的控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 12b8c166873802e3c0e6a8d4e73ff1b686229222
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>设置从“数据源”窗口中拖动时要创建的控件
你可以通过将某些项从创建数据绑定控件**数据源**窗口拖到 WPF 设计器或 Windows 窗体设计器。 在每个项**数据源**窗口具有时将其拖到设计器中创建的默认控件。 但是，你可以选择创建一个不同的控件。  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>设置为数据表或对象创建的控件  
拖动项表示数据表或对象从之前**数据源**窗口中，你可以选择一个控件中显示的所有数据或在单独控件中都显示每个列或属性。  
  
在此上下文中，术语*对象*指的是自定义业务对象、 实体 （在实体数据模型中） 或由服务返回的对象。  
  
### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>若要设置为数据表或对象创建的控件  
  
1.  请确保 WPF 设计器或 Windows 窗体设计器处于打开状态。  
  
2.  在**数据源**窗口中，选择的项目，表示数据表或对象你想要设置。  
  
3.  单击该项目的下拉列表菜单，然后单击菜单中的以下项之一：  
  
    -   若要在单独控件中显示每个数据字段，请单击**详细信息**。 当你将数据项拖动到设计器中时，此操作将创建一个不同的数据绑定控件，每个列或属性的父数据表或对象，以及为每个控件的标签。  
  
    -   若要显示的所有数据的单个控件中，选择一个不同的控件在列表中，如**DataGrid**或**列表**在 WPF 应用程序，或**DataGridView** Windows 窗体中应用程序。  
  
    可用控件列表取决于哪个设计器上已打开，.NET Framework 的版本将项目目标，以及是否已添加自定义控件绑定到该支持数据**工具箱**。 如果你想要创建的控件不在的可用控件列表中，你可以将控件添加到列表中。 有关详细信息，请参阅[将自定义控件添加到数据源窗口](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
    若要了解如何创建可添加到的数据表或对象中的控件列表的自定义 Windows 窗体控件**数据源**窗口中，请参阅[创建支持复杂数据的 Windows 窗体用户控件绑定](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)。  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>设置为数据列或属性创建的控件  
拖动项表示某一列或中的对象的属性之前**数据源**到设计器窗口中的，你可以设置要创建的控件。  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>若要设置为列或属性创建的控件  
  
1.  请确保 WPF 设计器或 Windows 窗体设计器处于打开状态。  
  
2.  在**数据源**窗口中，展开所需的表或对象以显示其列或属性。  
  
3.  选择你想要设置要创建控件的每个列或属性。  
  
4.  单击列或属性的下拉列表菜单，然后选择你想要创建时将项拖到设计器中的控件。  
  
     可用控件列表取决于哪个设计器上已打开，.NET Framework 的版本将项目目标，以及哪些自定义控件的支持数据绑定你已添加到**工具箱**。 如果你想要创建的控件的可用控件列表中，你可以将控件添加到列表中。 有关详细信息，请参阅[将自定义控件添加到数据源窗口](../data-tools/add-custom-controls-to-the-data-sources-window.md)。  
  
     若要了解如何创建可添加到的数据列或属性中的控件列表的自定义控件**数据源**窗口中，请参阅[创建支持简单数据绑定的Windows窗体用户控件](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     如果你不想要创建的列或属性的控件，选择**无**下拉列表菜单中。 如果你想要将父表或对象拖动到设计器中，但不是需要包含的特定列或属性，这非常有用。  
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)