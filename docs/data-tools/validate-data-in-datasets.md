---
title: "验证数据集中的数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0f328cbaac03680885bdbda97dff7bc9ac3cf2cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="validate-data-in-datasets"></a>验证数据集中的数据
数据进行验证是确认输入到数据对象的值符合中的数据集的架构的约束的过程。 验证过程还确认这些值是遵循已为你的应用程序设定的规则。 最好将更新发送到基础数据库之前的数据进行验证。 这将减少错误以及潜在应用程序和数据库之间的往返次数。  
  
你可以确认正在写入到数据集的数据是通过生成到数据集本身的验证检查有效。 数据集都可以检查无论方式更新的数据-不管是直接通过控件在表单中，在一个组件，或以某种其他方式。 因为数据集 （与不同数据库后端） 应用程序的一部分，它是逻辑的位置，若要生成应用程序特定的验证。  
  
将验证添加到你的应用程序的最佳时机是在数据集的分部类文件中。 在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]，打开**数据集设计器**双击你想要创建验证的列或表。 此操作将自动创建<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>事件处理程序。 
  
## <a name="validate-data"></a>验证数据  
 在数据集中的验证可以通过以下方式实现：  
  
-   通过创建自己可以在更改过程中检查各个数据列中的值的特定于应用程序验证。  有关详细信息，请参阅[如何： 将数据验证期间列更改](validate-data-in-datasets.md)。  
  
-   通过创建你自己可以检查为整个数据时的值的数据的应用程序特定验证更改行。 有关详细信息，请参阅[如何： 将数据验证期间行更改](validate-data-in-datasets.md)。  
  
-   通过为实际的架构定义的数据集的一部分，依此类推创建关键字、 唯一约束。 
  
-   通过设置的属性<xref:System.Data.DataColumn>对象，如<xref:System.Data.DataColumn.MaxLength%2A>， <xref:System.Data.DataColumn.AllowDBNull%2A>，和<xref:System.Data.DataColumn.Unique%2A>。  
  
多个事件引发由<xref:System.Data.DataTable>对象时在记录中正在发生的更改：  
  
-   <xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>期间和之后的单个列每次更改后，会引发事件。 <xref:System.Data.DataTable.ColumnChanging>事件非常有用，当你想要验证特定列中的更改。 有关建议更改的信息作为与事件自变量被传递。 
-   <xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>事件引发期间和之后任何行中的更改。 <xref:System.Data.DataTable.RowChanging>事件是更多常规。 它指示在行中，某个位置发生更改，但你不知道哪些列已更改。  
  
默认情况下，每次更改后的列因此引发四个事件。 第一种是<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>正在更改的特定列的事件。 接下来是<xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>事件。 如果对行进行了多个更改，将会针对每项更改引发事件。  
  
> [!NOTE]
>  数据行<xref:System.Data.DataRow.BeginEdit%2A>方法关闭<xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>每个单独的列更改后的事件。 在这种情况下，直到不引发该事件<xref:System.Data.DataRow.EndEdit%2A>已调用方法，当<xref:System.Data.DataTable.RowChanging>和<xref:System.Data.DataTable.RowChanged>只需一次引发事件。 有关详细信息，请参阅[填充数据集时关闭约束](../data-tools/turn-off-constraints-while-filling-a-dataset.md)。  
  
您选择的事件取决于想要验证的粒度级别。 如果这很重要立即列的更改时捕获错误，通过使用构建验证<xref:System.Data.DataTable.ColumnChanging>事件。 否则，请使用<xref:System.Data.DataTable.RowChanging>事件，这可能会导致在一次捕获多个错误。 此外，如果你的数据的结构，以便一个列的值验证基于另一列的内容，然后执行验证期间<xref:System.Data.DataTable.RowChanging>事件。
  
当更新记录时，<xref:System.Data.DataTable>对象引发事件发生的更改和进行更改之后可以响应。  
  
如果你的应用程序使用类型化数据集，你可以创建强类型的事件处理程序。 这会添加四个可以创建处理程序的其他类型化的事件： `dataTableNameRowChanging`， `dataTableNameRowChanged`， `dataTableNameRowDeleting`，和`dataTableNameRowDeleted`。 这些类型化的事件处理程序传递的参数，包括使代码更易于写入和读取你的表的列名称。  
  
## <a name="data-update-events"></a>数据更新事件  
  
|Event|描述|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|正在更改列中的值。 该事件，传递的行和列以及建议的新值。|  
|<xref:System.Data.DataTable.ColumnChanged>|列中的值已更改。 该事件，传递的行和列以及建议的值。|  
|<xref:System.Data.DataTable.RowChanging>|对所做的更改<xref:System.Data.DataRow>对象正准备提交回数据集。 如果尚未调用<xref:System.Data.DataRow.BeginEdit%2A>方法，<xref:System.Data.DataTable.RowChanging>事件引发到列的每项更改后立即<xref:System.Data.DataTable.ColumnChanging>引发事件。 如果调用<xref:System.Data.DataRow.BeginEdit%2A>在进行更改之前,<xref:System.Data.DataTable.RowChanging>仅在调用引发事件<xref:System.Data.DataRow.EndEdit%2A>方法。<br /><br /> 事件将行传递给你，以及一个值，该值所执行的操作 （更改、 插入和等等） 类型。|  
|<xref:System.Data.DataTable.RowChanged>|行已更改。 事件将行传递给你，以及一个值，该值所执行的操作 （更改、 插入和等等） 类型。|  
|<xref:System.Data.DataTable.RowDeleting>|正在删除行。 事件将行传递给你，以及一个值，该值所执行的操作 （删除） 类型。|  
|<xref:System.Data.DataTable.RowDeleted>|行已被删除。 事件将行传递给你，以及一个值，该值所执行的操作 （删除） 类型。|  
  
<xref:System.Data.DataTable.ColumnChanging>， <xref:System.Data.DataTable.RowChanging>，和<xref:System.Data.DataTable.RowDeleting>在更新过程中引发事件。 这些事件可用于验证数据或执行其他类型的处理。 由于发生这些事件期间，更新正在进行，您可以取消它通过引发异常，这会阻止从更新完成。  
  
<xref:System.Data.DataTable.ColumnChanged>，<xref:System.Data.DataTable.RowChanged>和<xref:System.Data.DataTable.RowDeleted>事件是更新已成功完成时引发的通知事件。 当你想要执行更多基于一次成功更新的操作时，这些事件非常有用。  
  
## <a name="validate-data-during-column-changes"></a>列更改过程中验证数据  
  
> [!NOTE]
>  **数据集设计器**创建可以在哪些验证逻辑添加到数据集分部类。 设计器生成数据集不会删除或更改的分部类中的任何代码。  
  
你可以在通过响应中的数据列的值更改时验证数据<xref:System.Data.DataTable.ColumnChanging>事件。 此事件时引发，传递的事件自变量 (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>)，其中包含所建议的当前列的值。 基于内容的`e.ProposedValue`，你可以：  
  
-   接受建议的值由不执行任何操作。  
  
-   通过设置列错误拒绝建议的值 (<xref:System.Data.DataRow.SetColumnError%2A>) 从在列更改事件处理程序。  
  
-   （可选） 使用<xref:System.Windows.Forms.ErrorProvider>控件以向用户显示一条错误消息。 有关详细信息，请参阅[ErrorProvider 组件](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)。  
  
此外可以在执行验证<xref:System.Data.DataTable.RowChanging>事件。 
  
## <a name="validate-data-during-row-changes"></a>行更改过程中验证数据  
你可以编写代码来确认你想要验证每个的列包含数据满足你的应用程序的要求。 执行此操作通过设置该列以指示其包含一个错误，是否建议的值是不可接受。 下面的示例设置了列错误时`Quantity`列是 0 或更小。 行更改事件处理程序应类似于下面的示例。  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>若要验证数据的行时更改 (Visual Basic)  
  
1.  打开中的数据集**数据集设计器**。 有关详细信息，请参阅[演练： 创建数据集设计器中的数据集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  双击要验证的表的标题栏。 此操作将自动创建<xref:System.Data.DataTable.RowChanging>事件处理程序<xref:System.Data.DataTable>数据集的分部类文件中。  
  
    > [!TIP]
    >  双击表名以创建行更改事件处理程序的左侧。 如果双击表名时，你可以对其进行编辑。  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>若要验证数据的行时更改 (C#)  
  
1.  打开中的数据集**数据集设计器**。 有关详细信息，请参阅[演练： 在数据集设计器中创建数据集](walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
2.  双击要验证的表的标题栏。 此操作将创建的分部类文件<xref:System.Data.DataTable>。  
  
    > [!NOTE]
    >  **数据集设计器**不会自动创建的事件处理程序<xref:System.Data.DataTable.RowChanging>事件。 你必须创建一个方法来处理<xref:System.Data.DataTable.RowChanging>挂钩中表的初始化方法的事件的事件，并运行的代码。  
  
3.  将下面的代码复制到该分部类中：  
  
    ```csharp  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## <a name="to-retrieve-changed-rows"></a>若要检索已更改的行  
数据表中的每行都有<xref:System.Data.DataRow.RowState%2A>属性，用于跟踪通过使用中的值的行的当前状态<xref:System.Data.DataRowState>枚举。 你可以从数据集或数据的表返回已更改的行，通过调用`GetChanges`方法<xref:System.Data.DataSet>或<xref:System.Data.DataTable>。 你可以验证在调用之前存在更改`GetChanges`通过调用<xref:System.Data.DataSet.HasChanges%2A>数据集的方法。 
  
> [!NOTE]
>  更改提交到数据集或数据的表后 (通过调用<xref:System.Data.DataSet.AcceptChanges%2A>方法)，则`GetChanges`方法不返回任何数据。 如果你的应用程序需要处理已更改的行，则必须处理的更改之前调用`AcceptChanges`方法。  
  
调用<xref:System.Data.DataSet.GetChanges%2A>的数据集或数据的表的方法返回一个新的数据集或数据表，包含已更改的唯一记录。 如果你想要获取特定的记录 — 例如，只是新记录或已修改的记录 — 可以将传递一个介于<xref:System.Data.DataRowState>枚举作为参数传递给`GetChanges`方法。  
  
使用<xref:System.Data.DataRowVersion>枚举，以访问行 （例如之前对其进行处理, 的行中的原始值） 的不同版本。  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>若要从数据集中获取所有已更改的记录  
  
-   调用<xref:System.Data.DataSet.GetChanges%2A>数据集的方法。  
  
     下面的示例创建新的数据集调用`changedRecords`并从调用的另一个数据集的所有更改记录使用填充它`dataSet1`。  
  
     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>若要获取所有已更改的记录的数据表  
  
-   调用<xref:System.Data.DataTable.GetChanges%2A>的数据表的方法。  
  
     下面的示例创建调用提供新数据表`changedRecordsTable`并从另一个数据表调用所有已更改的记录使用填充它`dataTable1`。  
  
     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>若要获取的特定行状态的所有记录  
  
-   调用`GetChanges`方法数据集或数据表并传入<xref:System.Data.DataRowState>作为自变量的枚举值。  
  
     下面的示例演示如何创建新的数据集调用`addedRecords`并仅使用已添加到的记录填充它`dataSet1`数据集。  
  
     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]  
  
     下面的示例演示如何返回最近添加到的所有记录`Customers`表：  
  
     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>访问数据行的原始版本  
数据集时对数据行进行更改，保留这两个原始 (<xref:System.Data.DataRowVersion.Original>) 和新 (<xref:System.Data.DataRowVersion.Current>) 行的版本。 例如，然后才能调用`AcceptChanges`方法，你的应用程序可以访问一条记录的不同版本 (中定义<xref:System.Data.DataRowVersion>枚举) 并进行相应处理所做的更改。  
  
> [!NOTE]
>  行的不同版本存在编辑的仅之后，并在它`AcceptChanges`调用方法。 后`AcceptChanges`调用方法、 当前和原始版本都相同。  
  
传递<xref:System.Data.DataRowVersion>值的列索引 （或字符串形式的列名称） 以及从该列的特定行版本中返回的值。 已更改的列标识期间<xref:System.Data.DataTable.ColumnChanging>和<xref:System.Data.DataTable.ColumnChanged>事件。 这是检查不同的行版本来进行验证的好时机。 但是，如果你已暂时挂起约束，不会引发这些事件，并且将需要以编程方式确定哪些列发生了更改。 你可以执行此操作通过循环访问<xref:System.Data.DataTable.Columns%2A>集合并比较不同<xref:System.Data.DataRowVersion>值。  
  
#### <a name="to-get-the-original-version-of-a-record"></a>若要获取一条记录的原始版本  
  
-   通过传入访问某一列的值<xref:System.Data.DataRowVersion>你想要返回的行。  
  
     下面的示例演示如何使用<xref:System.Data.DataRowVersion>要获取的原始值值`CompanyName`字段<xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>访问 DataRow 的当前版本  
  
#### <a name="to-get-the-current-version-of-a-record"></a>若要获取一条记录的当前版本  
  
-   访问某一列的值，并指示你想要返回哪个版本的行的索引中添加的参数。  
  
     下面的示例演示如何使用<xref:System.Data.DataRowVersion>要获取的当前值值`CompanyName`字段<xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]  
  
## <a name="see-also"></a>请参阅
[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)  
[如何： 验证 Windows 窗体 DataGridView 控件中的数据](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)   
[如何：使用 Windows 窗体 ErrorProvider 组件显示窗体验证的错误图标](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)