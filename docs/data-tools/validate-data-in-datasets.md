---
title: "验证数据集中的数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据验证"
  - "数据验证, 数据集"
  - "更新数据集, 验证数据"
  - "验证数据, 数据集"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 验证数据集中的数据
数据验证是指确认要输入数据对象中的值是否遵从数据集架构内的约束，以及是否遵从为应用程序所建立的规则的过程。  建议您在将更新信息发送到基础数据库前执行数据验证，这样可减少错误以及应用程序与数据库之间潜在的往返数据通信数。  通过将验证检查内置到数据集本身，可以确认写入数据集的数据是有效的。  无论如何执行更新（无论是由窗体中的控件直接执行，在组件中执行，还是以某种其他方式执行），数据集都可以检查数据。  由于数据集是应用程序的一部分，所以它是生成应用程序特定验证的合理位置（而不像在数据库后端内置相同的检查）。  
  
 要在应用程序中添加验证，建议您将其添加到程序集的分部类文件中。  在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，打开**“数据集设计器”**并双击要为其创建验证的列或表。  此操作自动创建 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件处理程序。  有关更多信息，请参见[如何：在列更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)或[如何：在行更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)。  有关完整示例，请参见[演练：向数据集添加验证](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md)。  
  
## 验证数据  
 数据集中的验证可以通过下列方式完成：  
  
-   通过创建您自己的应用程序特定的验证，该验证可以在对单个数据列中的值进行更改期间检查数据。  有关更多信息，请参见 [如何：在列更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)。  
  
-   通过创建您自己的应用程序特定的验证，该验证可以在整个数据行正在更改时对值进行更改期间检查数据。  有关更多信息，请参见 [如何：在行更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)。  
  
-   创建关键字、唯一约束等，将其作为数据集实际架构定义的一部分。  有关将验证的更多信息。架构定义中，请参见 [将 DataColumn 约束为包含唯一值](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint)。  
  
-   通过设置 <xref:System.Data.DataColumn> 对象的属性，例如 <xref:System.Data.DataColumn.MaxLength%2A>、<xref:System.Data.DataColumn.AllowDBNull%2A> 和 <xref:System.Data.DataColumn.Unique%2A>。  
  
 当在记录中发生更改时，<xref:System.Data.DataTable> 对象将会引发几个事件：  
  
-   每次更改单个列的过程中和其之后都会引发 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.ColumnChanged> 事件。  当要验证特定列中的更改时，<xref:System.Data.DataTable.ColumnChanging> 事件比较有用。  有关建议更改的信息将作为参数与事件一起传递。  有关更多信息，请参见 [如何：在列更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)。  
  
-   在行中进行任何更改的过程中和其之后都会引发 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。  <xref:System.Data.DataTable.RowChanging> 事件提供更为一般性的信息，因为它仅仅指示行中某处发生了更改，而您不知道哪一列已更改。  有关更多信息，请参见 [如何：在行更改过程中验证数据](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)。  
  
 因此，在默认情况下，每次更改列将引发四个事件：首先是针对将被更改的特定列的 <xref:System.Data.DataTable.ColumnChanging> 和 <xref:System.Data.DataTable.ColumnChanged> 事件，然后是 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。  如果对行进行了多项更改，则将为每项更改引发这些事件。  
  
> [!NOTE]
>  每次对单个列进行更改后，数据行的 <xref:System.Data.DataRow.BeginEdit%2A> 方法关闭 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。  这种情况下，在调用 <xref:System.Data.DataRow.EndEdit%2A> 方法之前将不会引发事件，此时只引发了一次 <xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowChanged> 事件。  有关更多信息，请参见[如何：在填充数据集时关闭约束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
 您选择的事件取决于您希望验证具有的间隔尺寸。  如果在更改列时立即捕获错误很重要，则应使用 <xref:System.Data.DataTable.ColumnChanging> 事件生成验证。  否则，应使用 <xref:System.Data.DataTable.RowChanging> 事件，它可能会导致立即捕获多个错误。  另外，如果按照数据的结构，将根据另一列的内容来验证一个列的值，则应该在 <xref:System.Data.DataTable.RowChanging> 事件过程中执行验证。  
  
 当更新记录时，<xref:System.Data.DataTable> 对象将引发事件，您可以在更改发生时和在更改完成后对这些事件作出响应。  
  
 如果应用程序正在使用类型化数据集，则可以创建强类型的事件处理程序。  这样将另外添加四种可为其创建处理程序的类型化事件：`dataTableNameRowChanging`、`dataTableNameRowChanged`、`dataTableNameRowDeleting` 和 `dataTableNameRowDeleted`。  这些类型化的事件处理程序会传递一个参数，它包含表的列名，使您可以更容易地读取和写入代码。  
  
## 数据更新事件  
  
|Event|说明|  
|-----------|--------|  
|<xref:System.Data.DataTable.ColumnChanging>|正在更改列中的值。  该事件向您传递行、列以及建议的新值。|  
|<xref:System.Data.DataTable.ColumnChanged>|已更改列中的值。  该事件向您传递行、列以及建议值。|  
|<xref:System.Data.DataTable.RowChanging>|对 <xref:System.Data.DataRow> 对象作出的更改将要提交回数据集。  如果尚未调用 <xref:System.Data.DataRow.BeginEdit%2A> 方法，那么紧接着引发 <xref:System.Data.DataTable.ColumnChanging> 事件之后，对列的每一更改都将引发 <xref:System.Data.DataTable.RowChanging> 事件。  如果在执行更改前确实调用了 <xref:System.Data.DataRow.BeginEdit%2A>，则仅当调用 <xref:System.Data.DataRow.EndEdit%2A> 方法时，才会引发 <xref:System.Data.DataTable.RowChanging> 事件。<br /><br /> 该事件向您传递此行和一个值，该值指示正在执行的操作类型（更改、插入等）。|  
|<xref:System.Data.DataTable.RowChanged>|已更改行。  该事件向您传递此行和一个值，该值指示正在执行的操作类型（更改、插入等）。|  
|<xref:System.Data.DataTable.RowDeleting>|正在删除行。  该事件向您传递此行和一个值，该值指示正在执行的操作类型（删除）。|  
|<xref:System.Data.DataTable.RowDeleted>|已删除行。  该事件向您传递此行和一个值，该值指示正在执行的操作类型（删除）。|  
  
 在更新过程中引发 <xref:System.Data.DataTable.ColumnChanging>、<xref:System.Data.DataTable.RowChanging> 和 <xref:System.Data.DataTable.RowDeleting> 事件。  您可以使用这些事件来验证数据或执行其他类型的处理。  由于在这些事件过程中更新正在进行，所以您可以通过引发异常（它将阻止更改完成）来取消更新。  
  
 <xref:System.Data.DataTable.ColumnChanged>、<xref:System.Data.DataTable.RowChanged> 和 <xref:System.Data.DataTable.RowDeleted> 事件是在更新成功完成后引发的通知事件。  当您需要基于成功的更新来执行进一步操作时，这些事件将十分有用。  
  
## 请参阅  
 [创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)   
 [如何：连接到数据库中的数据](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [如何：验证 Windows 窗体 DataGridView 控件中的数据](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [如何：使用 Windows 窗体 ErrorProvider 组件显示窗体验证的错误图标](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)