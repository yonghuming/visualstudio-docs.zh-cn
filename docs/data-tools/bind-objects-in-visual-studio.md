---
title: "将 Visual Studio 中的绑定对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 9f410fdfea8a241b10cbab621dbd781d3648a080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="bind-objects-in-visual-studio"></a>将 Visual Studio 中的绑定对象
Visual Studio 提供用于处理用作你的应用程序中的数据源的自定义对象的设计时工具。 如果你想要将绑定到 UI 控件的对象中存储数据库中的数据，建议的方法是使用实体框架生成的类。 实体框架自动生成的所有样本更改跟踪代码，这意味着，对本地对象的任何更改自动保存到数据库时在 DbSet 对象上调用 AcceptChanges。 有关详细信息，请参阅[实体框架文档](https://ef.readthedocs.org/en/latest/)。  
  
> [!TIP]
>  如果你的应用程序已基于数据集，仅应考虑到这篇文章中的对象绑定方法。如果你已熟悉数据集，并将处理你的数据是表格和不太复杂或太大，则还可以使用这些方法。 例如甚至更简单，涉及数据加载到对象直接，通过使用 DataReader 并手动更新 UI 而无需数据绑定，请参阅[使用 ADO.NET 创建简单的数据应用程序](../data-tools/create-a-simple-data-application-by-using-adonet.md)。  
  
## <a name="object-requirements"></a>对象要求  
 要处理的数据设计工具在 Visual Studio 中的自定义对象的唯一要求是对象需要至少一个公共属性。  
  
 通常情况下，自定义对象不需要任何特定的接口，构造函数或要作为应用程序的数据源属性。 但是，如果你想要将该对象从**数据源**到设计图面可创建一个数据绑定控件的窗口和如果对象实现<xref:System.ComponentModel.ITypedList>或<xref:System.ComponentModel.IListSource>接口，该对象必须具有默认值构造函数。 否则为 Visual Studio 无法实例化的数据源对象，并且你将项拖动到设计图面时，它会显示错误。  
  
## <a name="examples-of-using-custom-objects-as-data-sources"></a>作为数据源使用自定义对象的示例  
 尽管有无数的方式来实现应用程序逻辑，在使用作为数据源对象时，SQL 的情况下存在数据库是可以通过使用 Visual Studio 生成的 TableAdapter 对象来简化的几个标准操作。 本页介绍如何实现这些标准流程使用 TableAdapters.It 不旨在作为指南来创建自定义对象。 例如，你通常将执行以下的标准操作不考虑特定实现的对象或应用程序的逻辑：  
  
-   数据加载到对象 （通常是从数据库中）。  
  
-   创建类型化的对象集合。  
  
-   将对象添加到和从集合中删除对象。  
  
-   向窗体上的用户显示的对象数据。  
  
-   更改/编辑对象中的数据。  
  
-   将数据从对象保存回数据库。   
  
### <a name="load-data-into-objects"></a>将数据加载到对象  
 对于此示例，你将数据加载到你的对象使用 Tableadapter。 默认情况下，使用两种类型的方法，从数据库提取数据并填充数据表创建 Tableadapter。  
  
-   `TableAdapter.Fill`方法返回的数据填充现有数据表。  
  
-   `TableAdapter.GetData`方法返回一个新的数据集填充数据。  
  
 加载数据到自定义对象的最简单方法是调用`TableAdapter.GetData`方法，循环访问返回的数据表中的行的集合和填充每个对象每个行中的值。 你可以创建`GetData`返回任何查询添加到 TableAdapter 用于填充的数据表的方法。  
  
> [!NOTE]
>  Visual Studio 名称的 TableAdapter 查询`Fill`和`GetData`默认情况下，但这些名称可以更改为任何有效的方法名称。  
  
 下面的示例演示如何循环访问的数据表中中的行和并用数据填充对象：  
  
 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### <a name="create-a-typed-collection-of-objects"></a>创建对象的类型化的的集合  
 可以为您的对象，创建集合类，也可以使用自动提供的类型化的集合[BindingSource 组件](/dotnet/framework/winforms/controls/bindingsource-component)。  
  
 当你创建的自定义集合类的对象时，我们建议你从继承<xref:System.ComponentModel.BindingList%601>。 此泛型类提供功能来管理你的集合，以及能够引发将通知发送到 Windows 窗体中的数据绑定基础结构的事件。  
  
 中的自动生成集合<xref:System.Windows.Forms.BindingSource>使用<xref:System.ComponentModel.BindingList%601>其类型化的集合。 如果你的应用程序不需要附加功能，则你可以维护你的集合内<xref:System.Windows.Forms.BindingSource>。 有关详细信息，请参阅<xref:System.Windows.Forms.BindingSource.List%2A>属性<xref:System.Windows.Forms.BindingSource>类。  
  
> [!NOTE]
>  如果你的集合需要没有提供的基实现的功能<xref:System.ComponentModel.BindingList%601>，应创建自定义集合，因此你可以根据需要添加到类。  
  
 下面的代码演示如何创建强类型的集合类`Order`对象：  
  
 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### <a name="add-objects-to-a-collection"></a>将对象添加到集合  
 通过调用的对象添加到集合`Add`方法或你的自定义集合类的<xref:System.Windows.Forms.BindingSource>。  
  
 
> [!NOTE]
>  `Add`方法将自动提供给你的自定义集合时继承自<xref:System.ComponentModel.BindingList%601>。  
  
 下面的代码演示如何将对象添加到中的类型化集合<xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 下面的代码演示如何将对象添加到继承自的类型集合<xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  在此示例中`Orders`集合是的一个属性`Customer`对象。  
  
 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### <a name="remove-objects-from-a-collection"></a>从集合中删除对象  
 你从集合中删除对象通过调用`Remove`或`RemoveAt`方法或你的自定义集合类的<xref:System.Windows.Forms.BindingSource>。  
  
> [!NOTE]
>  `Remove`和`RemoveAt`方法自动提供为自定义集合，当从继承<xref:System.ComponentModel.BindingList%601>。  
  
 下面的代码演示如何找到并删除对象中的类型化集合<xref:System.Windows.Forms.BindingSource>与<xref:System.Windows.Forms.BindingSource.RemoveAt%2A>方法：  
  
 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### <a name="display-object-data-to-users"></a>向用户显示对象数据  
 若要显示中的对象添加到用户的数据，创建对象数据源使用**数据源配置**向导，然后将整个对象或单独的属性拖动到窗体从**数据源**窗口。  
  
### <a name="modify-the-data-in-objects"></a>修改对象中的数据  
 若要编辑自定义对象绑定到 Windows 窗体控件中的数据，只需编辑数据绑定控件中 （或直接在对象的属性中）。 数据绑定体系结构更新对象中的数据。  
  
 如果你的应用程序需要的更改跟踪和回滚建议的更改到其原始值，然后必须在对象模型中实现此功能。 有关如何数据表保持建议的更改跟踪的示例，请参阅<xref:System.Data.DataRowState>， <xref:System.Data.DataSet.HasChanges%2A>，和<xref:System.Data.DataTable.GetChanges%2A>。  
  
### <a name="save-data-in-objects-back-to-the-database"></a>将数据保存回数据库的对象中  
 通过将值从你的对象传递到 TableAdapter 的 DBDirect 方法将数据保存回数据库。  
  
 Visual Studio 创建可以直接对数据库执行的 DBDirect 方法。 这些方法不需要数据集或数据表的对象。  
  
|TableAdapter DBDirect 方法|描述|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|将新记录添加到数据库，允许您在单个列作为方法参数的值传递。|  
|`TableAdapter.Update`|更新现有数据库中的记录。 Update 方法使用原始和新列的值作为方法参数。 原始值中用于查找原始记录，并使用新值来更新该记录。<br /><br /> `TableAdapter.Update`方法还可用于协调数据集中的更改回数据库，通过执行<xref:System.Data.DataSet>， <xref:System.Data.DataTable>， <xref:System.Data.DataRow>，或数组<xref:System.Data.DataRow>的方法参数。|  
|`TableAdapter.Delete`|删除现有记录从基于作为方法参数中传递的原始列值的数据库。|  
  
 要保存的对象的集合中的数据，循环访问集合的对象 （例如，使用的下一步循环）。使用 TableAdapter 的 DBDirect 方法，将其发送到数据库的每个对象的值。  
  
 下面的示例演示如何使用`TableAdapter.Insert`DBDirect 方法，以添加新客户直接到数据库：  
  
 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)