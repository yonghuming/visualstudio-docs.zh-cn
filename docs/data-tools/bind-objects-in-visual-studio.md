---
title: "Visual Studio 中的对象绑定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "绑定, 到对象"
  - "数据 [Visual Studio], 绑定到对象"
  - "数据 [Visual Studio], 对象绑定"
  - "对象绑定"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual Studio 中的对象绑定
Visual Studio 提供设计时工具，可在应用程序中将自定义对象（相对于诸如实体、数据集和服务等其他数据源）作为数据源使用。  
  
## 对象要求  
 自定义对象与 Visual Studio 中的数据设计工具一起使用的唯一要求是，该对象需要至少一个公共属性。  
  
 通常，自定义对象不需要任何特定接口、构造函数或特性来充当应用程序的数据源。  但是，如果要将对象从**“数据源”**窗口拖到设计图面以创建数据绑定控件，并且对象实现 <xref:System.ComponentModel.ITypedList> 或 <xref:System.ComponentModel.IListSource> 接口，则对象必须具有默认构造函数（即无参数构造函数）。  否则，Visual Studio 将无法实例化数据源对象，并将会在您将项拖到设计图面时显示错误。  
  
## 使用自定义对象作为数据源的示例  
 将对象用作数据源时，虽然有无数种方法可实现应用程序逻辑，但是，通过使用由 Visual Studio 生成的 [TableAdapter](../data-tools/tableadapter-overview.md) 对象，只能简化很少的一部分标准操作。  本页解释如何使用 TableAdapter 实现这些标准操作；而不应用作创建自定义对象的指南。  例如，在不考虑对象的特定实现或应用程序逻辑的情况下，您通常执行以下标准操作：  
  
-   将数据加载到对象（通常来自数据库）中。  
  
-   创建对象的类型化集合。  
  
-   在集合中添加和移除对象。  
  
-   在窗体上向用户显示对象数据。  
  
-   更改\/编辑对象中的数据。  
  
-   将对象中的数据保存回数据库。  
  
> [!NOTE]
>  为更好地理解本页上的示例并为其提供上下文，建议您完成以下演练：[演练：连接到对象中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)。  该演练将创建本“帮助”页所讨论的对象。  
  
### 将数据加载到对象中  
 在此示例中，将使用 TableAdapter 将数据加载到对象中。  默认情况下，创建 TableAdapter 并使用它的以下两种方法来分别用于获取数据库中的数据和填充数据表。  
  
-   `TableAdapter.Fill` 方法使用返回的数据填充现有的数据表。  
  
-   `TableAdapter.GetData` 方法返回已填充数据的新数据表。  
  
 将数据加载到自定义对象的最简单的方法是调用 `TableAdapter.GetData` 方法，遍历所返回数据表的行集合，并用各行中的值填充各个对象。  可以创建 `GetData` 方法，该方法可为添加到 TableAdapter 中的任何查询均返回已填充的数据表。  
  
> [!NOTE]
>  默认情况下，Visual Studio 将 TableAdapter 查询命名为 `Fill` 和 `GetData`，但这些名称可以更改为任何有效的方法名称。  
  
 下面的示例演示如何遍历数据表中的行，并用数据填充对象：  
  
 有关完整的代码示例，请参见[演练：连接到对象中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)。  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### 创建对象的类型化集合  
 您可以为对象创建集合类，或使用由 [BindingSource 组件](../Topic/BindingSource%20Component.md) 自动提供的类型化集合。  
  
 为对象创建自定义集合类时，建议从 <xref:System.ComponentModel.BindingList%601> 继承。  此泛型类提供管理集合的功能，此外，它还能引发事件，这些事件可向 Windows 窗体中的数据绑定基础结构发送通知。  
  
 <xref:System.Windows.Forms.BindingSource> 中自动生成的集合对其类型化集合使用 <xref:System.ComponentModel.BindingList%601>。  如果应用程序不要求其他功能，则可以在 <xref:System.Windows.Forms.BindingSource> 中维护集合。  有关更多信息，请参见 <xref:System.Windows.Forms.BindingSource> 类的 <xref:System.Windows.Forms.BindingSource.List%2A> 属性。  
  
> [!NOTE]
>  如果 <xref:System.ComponentModel.BindingList%601> 的基实现提供不了集合要求的功能，则您应创建自定义集合，以便在需要时将其添加到类中。  
  
 下面的代码演示如何为 `Order` 对象的强类型集合创建类：  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### 向集合中添加对象  
 通过调用自定义集合类或 <xref:System.Windows.Forms.BindingSource> 的 `Add` 方法，可将对象添加到集合中。  
  
 有关使用 <xref:System.Windows.Forms.BindingSource> 向集合添加对象的示例，请参见[演练：连接到对象中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)中的 `LoadCustomers` 方法。  
  
 有关将向自定义集合添加对象的示例，请参见[演练：连接到对象中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)中的 `LoadOrders` 方法。  
  
> [!NOTE]
>  从 <xref:System.ComponentModel.BindingList%601> 继承时，将自动为您的自定义集合提供 `Add` 方法。  
  
 下面的代码演示如何向 <xref:System.Windows.Forms.BindingSource> 中的类型化集合添加对象：  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 下面的代码演示如何向从 <xref:System.ComponentModel.BindingList%601> 继承的类型化集合添加对象：  
  
> [!NOTE]
>  在此示例中，`Orders` 集合是 `Customer` 对象的属性。  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### 将对象从集合中移除  
 通过调用自定义集合类或 <xref:System.Windows.Forms.BindingSource> 的 `Remove` 或 `RemoveAt` 方法，可将对象从集合中移除。  
  
> [!NOTE]
>  从 <xref:System.ComponentModel.BindingList%601> 继承时，将自动为您的自定义集合提供 `Remove` 和 `RemoveAt` 方法。  
  
 下面的代码演示如何使用 <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> 方法，从 <xref:System.Windows.Forms.BindingSource> 中的类型化集合中定位并移除对象：  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### 向用户显示对象数据  
 若要向用户显示对象中的数据，请使用 [数据源配置向导](../data-tools/media/data-source-configuration-wizard.png) 创建对象数据源，然后从**“数据源”**窗口将整个对象或单个属性拖动到窗体上。  
  
 有关创建对象数据源的更多信息，请参见[如何：连接到对象中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)。  
  
 有关在 Windows 窗体上显示对象数据的更多信息，请参见 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
### 修改对象中的数据  
 若要编辑数据绑定到 Windows 窗体控件的自定义对象中的数据，只需编辑绑定控件中的数据（或直接在对象属性中编辑）即可。  数据绑定结构将更新对象中的数据。  
  
 如果应用程序要求跟踪更改并将建议的更改回滚为其原始值，则必须在对象模型中实现此功能。  有关数据表如何跟踪建议的更改的示例，请参见 <xref:System.Data.DataRowState>、<xref:System.Data.DataSet.HasChanges%2A> 和 <xref:System.Data.DataTable.GetChanges%2A>。  
  
### 将对象中的数据保存回数据库  
 通过将对象中的值传递到 TableAdapter 的 DBDirect 方法，可将数据保存回数据库。  
  
 Visual Studio 创建的 DBDirect 方法可直接对数据库执行操作。  这些方法不需要 DataSet 或 DataTable 对象。  
  
|TableAdapter DBDirect 方法|说明|  
|------------------------------|--------|  
|`TableAdapter.Insert`|向数据库中添加新记录，此方法允许将值作为方法参数传入各个列。|  
|`TableAdapter.Update`|更新数据库中的现有记录。  Update 方法将原始列值和新列值用作方法参数。  原始值用于定位原始记录，新值用于更新该记录。<br /><br /> 通过将 <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow>、或 <xref:System.Data.DataRow> 数组用作方法参数，`TableAdapter.Update` 方法还可用于将数据集中的更改协调回数据库。|  
|`TableAdapter.Delete`|在基于作为方法参数传入的原始列值的数据库中，删除其现有记录。|  
  
 若要保存对象集合中的数据，请遍历该对象集合（例如，使用 for\-next 循环），然后使用 TableAdapter 的 DBDirect 方法将每个对象的值发送到数据库中。  
  
 下面的示例演示如何使用 `TableAdapter.Insert` DBDirect 方法将新客户直接添加到数据库中：  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## 请参阅  
 [如何：连接到对象中的数据](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [演练：连接到对象中的数据（Windows 窗体）](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [如何：将数据从对象保存到数据库](../data-tools/save-data-from-an-object-to-a-database.md)   
 [如何：使用 TableAdapter 直接访问数据库](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [演练：用 TableAdapter DBDirect 方法保存数据](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [保存数据](../data-tools/saving-data.md)