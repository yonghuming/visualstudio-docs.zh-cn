---
title: "分层更新 |Microsoft 文档"
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
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0091e17cf24a9476dde84cf2d8ad1a34f94e2cdd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="hierarchical-update"></a>分层更新
*分层更新*指的维护引用完整性规则时保存更新后的数据 （具有两个或多个相关表的数据集） 回数据库的过程。 *引用完整性*指由控制插入、 更新和删除相关的记录的行为在数据库中的约束的一致性规则。 例如，它是强制执行之前允许该客户的订单来创建客户记录的创建的引用完整性。  有关数据集中的关系的详细信息，请参阅[数据集中的关系](../data-tools/relationships-in-datasets.md)  
  
 分层更新功能使用`TableAdapterManager`管理`TableAdapter`中类型化数据集。 `TableAdapterManager`组件是[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-生成的类，使其不属于[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 当将表从数据源窗口拖动到 Windows 窗体或在 WPF 页中时，Visual Studio 将 TableAdapterManager 类型的变量添加到窗体或页面，并在组件栏中的设计器中查看它。 有关详细信息`TableAdapterManager`类，请参阅的 TableAdapterManager 引用部分[Tableadapter](../data-tools/create-and-configure-tableadapters.md)。  
  
 默认情况下，数据集视为相关的表"仅，关系"这意味着它并不强制外键约束。 可以通过使用数据集设计器来修改在设计时该设置。 选择要显示的两个表之间的关系行**关系**对话框。 您在此处进行的更改将确定 TableAdapterManager 行为时它将更改的相关表中发送回数据库。  
  
## <a name="enable-hierarchical-update-in-a-dataset"></a>启用数据集中的分层更新  
 默认情况下，所有新的数据集添加列表或项目中创建的情况下启用分层更新。 通过设置打开或关闭分层更新**分层更新**到的数据集的类型化数据集属性**True**或**False**:  
  
 ![分层更新设置](../data-tools/media/hierarchical-update-setting.png "分层更新设置")  
  
## <a name="create-a-new-relation-between-tables"></a>创建表之间的新关系  
 若要创建两个表之间的新关系，在数据集设计器中，选择每个表的标题栏，然后右键单击并选择**添加关系**。  
  
 ![分层更新添加关系菜单](../data-tools/media/hierarchical-update-add-relation-menu.png "分层更新添加关系菜单")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>了解 foreign key 约束，级联更新和删除  
 务必了解如何 foreign key 约束，以及生成的数据集代码创建的级联在数据库中的行为。  
  
 默认情况下，数据数据表的数据集生成关系 (<xref:System.Data.DataRelation>) 的匹配数据库中的关系。 但是，在数据集中的关系不生成作为外键约束。 <xref:System.Data.DataRelation>配置为**关系仅**而无需<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>或<xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>生效。  
  
 默认情况下，级联更新和级联删除操作被关闭状态中，即使数据库关系设置级联更新和/或级联删除开启。 例如，创建新的客户和新订单，然后尝试将数据保存可能导致冲突与数据库中定义的外键约束。 有关详细信息，请参阅[填充数据集时关闭约束](turn-off-constraints-while-filling-a-dataset.md)。  
  
## <a name="set-the-order-to-perform-updates"></a>设置以执行更新的顺序  
 设置顺序，以便执行更新集的各顺序插入、 更新和删除，需要将所有已修改的数据保存在数据集的所有表。 启用分层更新后，插入进行第一次，然后更新，，然后删除。 `TableAdapterManager`提供`UpdateOrder`可以是组以执行更新第一次，然后插入和删除的属性。  
  
> [!NOTE]
>  请务必了解，更新顺序是全包含所有权限。 也就是说，当执行更新，插入和删除将执行的数据集中的所有表。  
  
 若要设置`UpdateOrder`属性，则请将某些项从[数据源窗口](add-new-data-sources.md)拖到窗体中，选择`TableAdapterManager`在组件栏，然后将设置`UpdateOrder`中的属性**属性**窗口。 
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>在执行分层更新之前创建数据集的备份副本  
 在您保存数据 (通过调用`TableAdapterManager.UpdateAll()`方法)，则`TableAdapterManager`尝试更新单个事务中每个表的数据。 如果任何表的更新的任何部分失败，将回滚整个事务。 在大多数情况下，回滚返回到其原始状态应用程序。  
  
 但是，有时你可能想要从备份副本还原数据集。 在你使用自动递增值时，可能会出现这样的一个例子。 例如，如果保存操作未成功、 自动递增的值不会重置数据集和数据集将继续创建自动递增的值。这将使可能不是在你的应用程序中可接受编号中存在间隔。 在情况下这种问题，`TableAdapterManager`提供`BackupDataSetBeforeUpdate`用备份副本替换现有数据集，如果事务失败时的属性。  
  
> [!NOTE]
>  备份副本是在内存中时`TableAdapterManager.UpdateAll`方法是否正在运行。 因此，没有以编程方式访问此备份的数据集因为它将替换原始数据集或超出范围就会立即`TableAdapterManager.UpdateAll`方法完成运行。  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>修改生成保存代码以执行分层更新  
 通过调用 `TableAdapterManager.UpdateAll` 方法并传入包含相关表的数据集的名称，可将数据集中相关数据表的更改保存到数据库。 例如，运行 `TableAdapterManager.UpdateAll(NorthwindDataset)` 方法将 NorthwindDataset 中所有表的更新发送到后端数据库。  
  
 拖放项从后**数据源**窗口中，代码会自动添加到`Form_Load`事件以填充每个表 (`TableAdapter.Fill`方法)。 此外将代码添加到**保存**按钮单击事件的<xref:System.Windows.Forms.BindingNavigator>将数据从数据集保存回数据库 (`TableAdapterManager.UpdateAll`方法)。  
  
 生成的保存代码还包含调用 `CustomersBindingSource.EndEdit` 方法的一行代码。 更具体地说，它调用<xref:System.Windows.Forms.BindingSource.EndEdit%2A>方法的第一个<xref:System.Windows.Forms.BindingSource>，它将添加到窗体。 换而言之，此代码只为生成第一个表拖动从**数据源**拖到窗体的窗口。 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 调用将提交当前正在编辑的任何数据绑定控件中的所有更改。 因此，如果数据绑定控件仍然具有焦点并且单击**保存**按钮，所有挂起的编辑，因为在执行真正的保存之前提交事务，控件 (`TableAdapterManager.UpdateAll`方法)。  
  
> [!NOTE]
>  数据集设计器仅添加`BindingSource.EndEdit`放到窗体的第一个表的代码。 因此，必须对窗体上的每个相关表添加一行调用 `BindingSource.EndEdit` 方法的代码。 对于本演练，这意味着你必须添加一个对 `OrdersBindingSource.EndEdit` 方法的调用。  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>更新代码以在保存前提交对相关表的更改  
  
1.  双击**保存**按钮上<xref:System.Windows.Forms.BindingNavigator>以打开**Form1**在代码编辑器中。  
  
2.  在调用 `OrdersBindingSource.EndEdit` 方法的代码行后添加一行调用 `CustomersBindingSource.EndEdit` 方法的代码。 中的代码**保存**按钮单击事件应如下所示：  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]  
  
除了在将数据保存到数据库之前提交对相关子表的更改外，你可能还需要在向数据集添加新子记录之前先提交新创建的父记录。 也就是说，你可能需要先向数据集添加新父记录 (Customer)，然后外键约束才允许将新子记录 (Orders) 添加到数据集中。 为实现这一点，可以使用子 `BindingSource.AddingNew` 事件。  
  
> [!NOTE]
>  你是否必须提交新父记录取决于用于绑定到数据源的控件的类型。 在本演练中，你可以使用单独的控件绑定到父表。 这需要额外的代码来提交新的父记录。 如果父记录相反的复杂绑定控件中显示类似如下<xref:System.Windows.Forms.DataGridView>、 额外<xref:System.Windows.Forms.BindingSource.EndEdit%2A>调用父记录不是必需的。 这是因为这类控件的基础数据绑定功能可以提交新记录。  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>添加代码以在添加新子记录之前在数据集中提交父记录  
  
1.  为 `OrdersBindingSource.AddingNew` 事件创建一个事件处理程序。  
  
    -   打开**Form1**在设计视图中，选择**OrdersBindingSource**在组件栏中，选择**事件**中**属性**窗口中，和然后双击**AddingNew**事件。  
  
2.  将代码行添加到的事件处理程序调用`CustomersBindingSource.EndEdit`方法。 `OrdersBindingSource_AddingNew` 事件处理程序中的代码应如下所示：  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]  
  
## <a name="tableadaptermanager-reference"></a>TableAdapterManager 引用  
 默认情况下，`TableAdapterManager`创建包含相关的表的数据集时，将生成类。 若要阻止生成类，将更改的值`Hierarchical Update`为 false 的数据集的属性。 当拖动到设计图面上的 Windows 窗体或在 WPF 页的关系的表时，Visual Studio 将声明类的成员变量。 如果你不使用数据绑定时，你必须手动将该变量的声明。  
  
 `TableAdapterManager`类不是属于[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。 因此，你不能查找其文档中。 在设计时数据集创建过程的一部分创建。  
  
 以下是常用的方法和属性`TableAdapterManager`类：  
  
|成员|描述|  
|------------|-----------------|  
|`UpdateAll` 方法|将保存数据的所有表中的所有数据。|  
|`BackUpDataSetBeforeUpdate` 属性|确定是否在执行前创建数据集的备份副本`TableAdapterManager.UpdateAll`方法。布尔值。|  
|*tableName* `TableAdapter`属性|表示`TableAdapter`。 生成`TableAdapterManager`包含每个属性`TableAdapter`它所管理。 例如，具有 Customers 和 Orders 表的数据集生成与`TableAdapterManager`包含`CustomersTableAdapter`和`OrdersTableAdapter`属性。|  
|`UpdateOrder` 属性|控制单个 insert、 update 和 delete 命令的顺序。 将此属性设置为中的值之一`TableAdapterManager.UpdateOrderOption`枚举。<br /><br /> 默认情况下，`UpdateOrder`设置为**InsertUpdateDelete**。 这意味着，它将插入，然后更新，然后删除数据集中的所有表执行。|  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)