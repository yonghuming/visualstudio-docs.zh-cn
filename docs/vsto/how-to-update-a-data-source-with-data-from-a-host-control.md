---
title: "如何：使用宿主控件中的数据更新数据源"
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
  - "文档 [Visual Studio 中的 Office 开发]，数据源更新"
  - "数据 [Visual Studio 中的 Office 开发]，从文档中更新数据源"
  - "宿主控件 [Visual Studio 中的 Office 开发]，数据源更新"
  - "Office 文档 [Visual Studio 中的 Office 开发]，数据源"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：使用宿主控件中的数据更新数据源
  可以将宿主控件绑定到数据源，然后使用在此控件中对数据所做的更改来更新该数据源。 此过程包括以下两个主要步骤：  
  
1.  使用控件中的已修改数据更新内存中数据源。 通常情况下，内存中数据源是一个 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或某个其他数据对象。  
  
2.  使用内存中数据源中的已更改数据更新数据库。 此步骤仅适用于数据源连接到后端数据库（例如 SQL Server 或 Microsoft Office Access 数据库）的情况。  
  
 有关宿主控件和数据绑定的详细信息，请参阅[宿主项和宿主控件概述](../vsto/host-items-and-host-controls-overview.md)和[将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## 更新内存中数据源  
 默认情况下，支持简单数据绑定的宿主控件（例如 Word 文档中的内容控件或 Excel 工作表中的命名范围控件）不将数据更改保存到内存中数据源。 也就是说，如果最终用户更改宿主控件中的某个值后离开此控件，则该控件中的这个新值并不会自动保存到数据源中。  
  
 若要将数据保存到数据源，可以编写更新数据源的代码以响应运行时的某个特定事件，或者可以将控件配置为当控件中的值更改时自动更新数据源。  
  
 无需将 <xref:Microsoft.Office.Tools.Excel.ListObject> 更改保存到内存中数据源。 如果将 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件绑定到数据，则 <xref:Microsoft.Office.Tools.Excel.ListObject> 控件会自动将更改保存到内存中数据源，而无需借助其他代码。  
  
#### 在运行时更新内存中数据源  
  
-   调用将控件绑定到数据源的 <xref:System.Windows.Forms.Binding> 对象的 <xref:System.Windows.Forms.Binding.WriteValue%2A> 方法。  
  
     下面的示例将在 Excel 工作表中对 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件所做的更改保存到数据源。 此示例假定你有一个名为 `namedRange1` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，且其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性已绑定到数据源中的一个字段。  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### 自动更新内存中数据源  
 你可也可以配置控件，使其自动更新内存中数据源。 在文档级项目中，可以通过使用代码或设计器来实现。 而在 VSTO 外接程序项目中，则必须使用代码来实现。  
  
##### 通过使用代码将控件设置为自动更新内存中数据源  
  
1.  使用将控件绑定到数据源的 <xref:System.Windows.Forms.Binding> 对象的 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  模式。 有两个选项可用于更新数据源：  
  
    -   若要在验证控件时更新数据源，请将此属性设置为 System.Windows.Forms.DataSourceUpdateMode.OnValidation。  
  
    -   若要在控件的数据绑定属性值更改时更新数据源，请将此属性设置为 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged。  
  
        > [!NOTE]  
        >  因为 Word 不提供文档更改或控件更改通知，所以 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged 选项不适用于 Word 宿主控件。 但是，此选项可用于 Word 文档中的 Windows 窗体控件。  
  
     下面的示例将 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件配置为当该控件中的值更改时自动更新数据源。 此示例假定你有一个名为 `namedRange1` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控件，且其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 属性已绑定到数据源中的一个字段。  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### 通过使用设计器将控件设置为自动更新内存中数据源  
  
1.  在 Visual Studio 的设计器中，打开 Word 文档或 Excel 工作簿。  
  
2.  单击希望其自动更新数据源的控件。  
  
3.  在“属性”窗口中，展开“\(DataBindings\)”属性。  
  
4.  在“\(Advanced\)”属性旁边，单击省略号按钮 \(![VisualStudioEllipsesButton 屏幕快照](~/docs/vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton 屏幕快照")\)。  
  
5.  在“格式设置和高级绑定”对话框中，单击“数据源更新模式”下拉列表并选择以下值之一：  
  
    -   若要在验证控件时更新数据源，请选择“OnValidation”。  
  
    -   若要在控件的数据绑定属性值更改时更新数据源，请选择“OnPropertyChanged”。  
  
        > [!NOTE]  
        >  因为 Word 不提供文档更改或控件更改通知，所以“OnPropertyChanged”选项不适用于 Word 宿主控件。 但是，此选项可用于 Word 文档中的 Windows 窗体控件。  
  
6.  关闭“格式设置和高级绑定”对话框。  
  
## 更新数据库  
 如果内存中数据源与某个数据库关联，则必须使用对该数据源所做的更改来更新此数据库。 有关更新数据库的详细信息，请参阅[将数据保存在数据集中](../Topic/Saving%20data%20back%20to%20the%20database.md)和[如何：使用 TableAdapter 更新数据](../data-tools/update-data-by-using-a-tableadapter.md)。  
  
#### 更新数据库  
  
1.  调用控件的 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法。  
  
     在设计时将数据绑定控件添加到文档或工作簿时，会自动生成 <xref:System.Windows.Forms.BindingSource>。<xref:System.Windows.Forms.BindingSource> 将该控件连接到项目中的类型化数据集。 有关详细信息，请参阅[BindingSource 组件概述](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)。  
  
     下面的代码示例假定你的项目包含一个名为 `customersBindingSource` 的 <xref:System.Windows.Forms.BindingSource>。  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  调用在项目中生成的 TableAdapter 的 `Update` 方法。  
  
     在设计时将数据绑定控件添加到文档或工作簿时，会自动生成 TableAdapter。TableAdapter 将项目中的类型化数据集连接到数据库。 有关详细信息，请参阅[TableAdapter 概述](/visual-studio/data-tools/tableadapter-overview)。  
  
     下面的代码示例假定你具有与 Northwind 数据库中的 Customers 表的连接，并且你的项目包含一个名为 `customersTableAdapter` 的 TableAdapter 和一个名为 `northwindDataSet` 的类型化数据集。  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## 请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [将数据保存在数据集中](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [如何：使用 TableAdapter 更新数据](../data-tools/update-data-by-using-a-tableadapter.md)   
 [如何：在工作表中滚动查看数据库记录](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [如何：用数据库中的数据填充工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何：用对象中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：用服务中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  