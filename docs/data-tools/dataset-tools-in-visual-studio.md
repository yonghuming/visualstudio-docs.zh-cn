---
title: "在 Visual Studio 中使用数据集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "缓存 [Visual Studio], 数据集"
  - "区分大小写, 数据集"
  - "子记录"
  - "约束 [Visual Basic], 数据集"
  - "数据集中的当前记录"
  - "数据适配器, 填充数据集"
  - "数据缓存, 数据集"
  - "数据关系"
  - "数据库 [Visual Basic], 更新"
  - "DataRelation 对象, 数据集"
  - "DataSet 类"
  - "DataSet 类, 关于数据集"
  - "数据集 [Visual Basic]"
  - "数据集 [Visual Basic], 扩展属性"
  - "数据集 [Visual Basic], 填充"
  - "数据集 [Visual Basic], msprop"
  - "数据集 [Visual Basic], namespace"
  - "数据集 [Visual Basic], 填充"
  - "数据集 [Visual Basic], 关系"
  - "扩展属性, 在类型化的数据集中"
  - "外键, 数据集"
  - "主-详细信息表, 数据集"
  - "msprop"
  - "数据集中的父记录"
  - "相关表"
  - "相关表, 数据集"
  - "关系, 数据集"
  - "架构 [Visual Basic], 数据集"
  - "类型化数据集"
  - "类型化数据集, 与非类型化数据集比较"
  - "唯一约束（数据集）"
  - "非类型化数据集"
  - "非类型化数据集, 与类型化数据集比较"
  - "更新数据集, 关于数据集更新"
  - "XML [Visual Basic], 数据集"
  - "XML 架构, 关于 XML 架构和数据集"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual Studio 中使用数据集
数据集是包含数据表的对象，可以在这些数据表中临时存储数据以便在应用程序中使用。  如果应用程序要求使用数据，则可以将该数据加载到数据集中，数据集在本地内存中为应用程序提供了待用数据的缓存。  即使应用程序从数据库断开连接，也可以使用数据集中的数据。  数据集维护有关其数据的更改的信息，因此可以跟踪数据更新，并在应用程序重新连接时将更新发送回数据库。  
  
 以下主题提供有关在 Visual Studio 中使用数据集的详细信息：  
  
|主题|说明|  
|--------|--------|  
|[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)|介绍用于创建数据集的设计时工具。|  
|[如何：创建类型化数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)|介绍如何在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中使用设计工具创建类型化数据集。|  
|[如何：扩展数据集的功能](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|提供创建数据集的分部类（可以在其中添加除设计器生成的代码之外的代码）的步骤。|  
|[如何：在数据集设计器中打开数据集](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|介绍如何从**“解决方案资源管理器”**和**“数据源”**窗口打开数据集。|  
|[如何：编辑数据集](../Topic/How%20to:%20Edit%20a%20Dataset.md)|介绍如何使用**“数据集设计器”**编辑数据集中的对象。|  
|[演练：使用数据集设计器创建数据集](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|提供分步说明，介绍如何在不使用**“数据源配置向导”**的情况下创建类型化数据集。|  
|[设计数据表](../data-tools/designing-datatables.md)|提供相关主题的链接，介绍如何使用设计时工具创建和编辑数据表。|  
|[数据集中的关系](../data-tools/relationships-in-datasets.md)|提供相关主题的链接，介绍如何使用设计时工具创建和编辑数据关系。|  
|[TableAdapter](../Topic/TableAdapters.md)|提供相关主题的链接，介绍如何使用设计时工具创建和编辑 TableAdapter。|  
|[在 N 层应用程序中使用数据集](../data-tools/work-with-datasets-in-n-tier-applications.md)|介绍什么是 n 层应用程序，以及哪些功能可用于在 n 层应用程序中处理数据集。|  
  
 <xref:System.Data.DataSet> 的结构类似于关系数据库的结构；它公开表、行、列、约束和关系的分层对象模型。  
  
 数据集可以类型化或非类型化。  （有关更多信息，请参见下面标题为“类型化数据集与非类型化数据集”一节中的内容。）类型化数据集的架构（表和列结构）派生自 .xsd 文件，并且易于对其进行编程。  在应用程序中既可以使用类型化数据集也可以使用非类型化数据集。  不过，Visual Studio 对类型化数据集提供了更多工具支持，而且使用类型化数据集进行编程不仅更加简单，而且不易出错。  
  
 创建类型化数据集的方法是运行 [数据源配置向导](../data-tools/media/data-source-configuration-wizard.png)，或通过**“项目”**菜单上的**“添加新项”**命令来添加**“数据集”**项。  有关更多信息，请参见[如何：创建类型化数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
 创建非类型化数据集的方法是将**“数据集”**项从**“工具箱”**拖动到 [Windows Forms Designer](http://msdn.microsoft.com/zh-cn/3c3d61f8-f36c-4d41-b9c3-398376fabb15)或[Component Designer](../Topic/Component%20Designer.md)上。  
  
 创建数据集后，在[创建和编辑类型化数据集](../data-tools/creating-and-editing-typed-datasets.md)中进行编辑。  
  
 可以使用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 命名空间的以下部分创建和使用类型化和非类型化数据集。  
  
 ![系统数据数据集命名空间](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
数据集位于 System.Data 命名空间中  
  
 数据集的对象通过标准编程构造（如属性和集合）向您公开。  例如：  
  
-   <xref:System.Data.DataSet> 类包含数据表的 <xref:System.Data.DataTableCollection> 集合和 <xref:System.Data.DataRelation> 对象的 <xref:System.Data.DataRelationCollection> 集合。  
  
-   <xref:System.Data.DataTable> 类包含表行的 <xref:System.Data.DataRowCollection> 集合、数据列的 <xref:System.Data.DataColumnCollection> 集合和数据关系的 <xref:System.Data.DataTable.ChildRelations%2A> 和 <xref:System.Data.DataTable.ParentRelations%2A> 集合。  
  
-   <xref:System.Data.DataRow> 类包含 <xref:System.Data.DataRow.RowState%2A> 属性，该属性的值指示数据表自首次从数据库加载以来，行是否已更改以及是如何更改的。  <xref:System.Data.DataRow.RowState%2A> 属性的可能值包括 <xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState>。  
  
## 用数据填充数据集  
 默认情况下，数据集不包含任何实际数据。  实际上，用数据填充数据集指的是将数据加载到组成数据集的 <xref:System.Data.DataTable> 对象中。  可以通过执行 TableAdapter 查询或数据适配器（例如 <xref:System.Data.SqlClient.SqlDataAdapter>）命令来填充数据表。  对数据集填充数据时，将引发各种事件，并对约束进行检查，等等。  有关向数据集加载数据的更多信息，请参见[将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)。  
  
 在将项从[“数据源”窗口](../Topic/Data%20Sources%20Window.md)拖动到 Windows 应用程序中的窗体上时，填充数据集的代码会自动添加到窗体加载事件处理程序中。  有关更多信息，请完成下面的演练：[演练：在 Windows 窗体上显示数据](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)。  
  
 使用 TableAdapter 填充数据集的示例：  
  
 [!CODE [VbRaddataDatasets#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#1)]  
  
 可以用多种方法填充数据集：  
  
-   如果使用设计时工具（如数据向导之一）创建了数据集，则请调用 TableAdapter 的 `Fill` 方法。  （TableAdapter 通过默认的 `Fill` 方法创建，但由于其名称是可以更改的，因此实际的方法名称可能有所不同。）有关更多信息，请参见[如何：使用数据填充数据集](../data-tools/how-to-fill-a-dataset-with-data.md)中的“使用 TableAdapter 填充数据集”一节。  
  
-   调用 <xref:System.Data.Common.DataAdapter> 的 `Fill` 方法。  有关更多信息，请参见[从 DataAdapter 填充 DataSet](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md)。  
  
-   通过创建 <xref:System.Data.DataRow> 对象并将它们添加到表的 <xref:System.Data.DataRowCollection> 集合，可手动填充数据集中的表。  （只能在运行时执行此操作，无法在设计时设置 <xref:System.Data.DataRowCollection> 集合。）有关更多信息，请参见[向数据表中添加数据](../Topic/Adding%20Data%20to%20a%20DataTable.md)。  
  
-   将 XML 文档或流读入数据集。  有关更多信息，请参见 <xref:System.Data.DataSet.ReadXml%2A> 方法。  有关示例，请参见[演练：将 XML 数据读取到数据集](../data-tools/read-xml-data-into-a-dataset.md)。  
  
-   合并（复制）一个程序集与另一个数据集的内容。  如果应用程序从不同的来源（例如，不同的 XML Web services）获取数据集，但是需要将它们合并为一个数据集，该方案会很有用。  有关更多信息，请参见 [合并 DataSet 内容](../Topic/Merging%20DataSet%20Contents.md)。  
  
-   合并（复制）两个 <xref:System.Data.DataTable> 的内容。  
  
## 将数据集中的数据保存回数据库  
 当数据集中的记录发生更改时，这些更改必须写回数据库。  要将更改从数据集写入数据库，请调用负责在数据集与相应的数据库之间通信的 TableAdapter 或 <xref:System.Data.Common.DataAdapter> 的 `Update` 方法。  
  
 在 Visual Studio 中使用数据设计工具时，通过调用 TableAdapter 的 Update 方法并传入要保存的数据表来将数据发送回数据库。  例如：  
  
 [!CODE [VbRaddataDatasets#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#2)]  
  
 若要更精细地控制更新过程，请调用 TableAdapter 的 DBDirect 方法之一，这些方法可以为每个数据行分别传入值。  有关更多信息，请参见[如何：使用 TableAdapter 更新数据](../data-tools/update-data-by-using-a-tableadapter.md)和[演练：用 TableAdapter DBDirect 方法保存数据](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)。  
  
 用于操作单个记录的 <xref:System.Data.DataRow> 类包含 <xref:System.Data.DataRow.RowState%2A> 属性，该属性的值指示数据表自首次从数据库加载后，行是否已更改以及是如何更改的。  可能的值包括 <xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState> 和 <xref:System.Data.DataRowState>。  TableAdapter 和 <xref:System.Data.Common.DataAdapter> 的 `Update` 方法检查 <xref:System.Data.DataRow.RowState%2A> 属性的值，以确定哪些记录需要写入数据库，以及应调用哪个数据库命令（`InsertCommand`、`UpdateCommand` 和 `DeleteCommand`）。  
  
 有关更新数据的更多信息，请参见[保存数据](../data-tools/saving-data.md)。  
  
## 在数据集中导航记录  
 因为数据集是完全断开连接的数据容器，所以数据集（与 ADO 记录集不同）不支持当前记录的概念。  相反，数据集中的所有记录在任何时候都可用。  
  
 由于没有当前记录，因此就没有指向当前记录的特定属性，也没有从一个记录移动到另一个记录的方法或属性（请参见下面的说明）。  可以访问数据集中以对象形式出现的各个表；每个表公开一个行集合。  可以像处理任何集合那样处理行集合，通过集合的索引访问行，或者在编程语言中使用特定于集合的语句来访问行。  
  
 例如，可使用以下代码获取 `Customers` 表的第四行：  
  
 [!CODE [VbRaddataDatasets#3](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#3)]  
  
> [!NOTE]
>  如果正在将窗体中的控件绑定到数据集，则可以使用 <xref:System.Windows.Forms.BindingNavigator> 组件简化对单个记录的访问。  有关更多信息，请参见[如何：在 Windows 窗体中导航数据](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md)。  
  
## LINQ to Dataset  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] 支持对 <xref:System.Data.DataSet> 对象中的数据执行[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。  有关更多信息，请参见 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)。  
  
## 数据集和 XML  
 数据集是数据的关系视图，可用 XML 表示。  数据集和 XML 之间的这种关系使您可以从数据集的以下功能中获益：  
  
-   数据集的结构（表、列、关系和约束）可在 XML 架构中定义。  数据集可以使用 <xref:System.Data.DataSet.ReadXmlSchema%2A> 和 <xref:System.Data.DataSet.WriteXmlSchema%2A> 方法读写存储结构化信息的架构。  如果没有可用的架构，则数据集可以从关系结构的 XML 文档中的数据推导（通过其 <xref:System.Data.DataSet.InferXmlSchema%2A> 方法）出一个架构。  有关 XML 架构的更多信息，请参见[生成 XML 架构](../Topic/Building%20XML%20Schemas.md)。  
  
-   可以生成一个数据集类，在其中合并架构信息以定义其数据结构。  这种数据集也称为*“类型化”*数据集。  有关创建类型化数据集的信息，请参见[如何：创建类型化数据集](../data-tools/create-and-configure-datasets-in-visual-studio.md)。  
  
-   可以使用数据集的 <xref:System.Data.DataSet.ReadXml%2A> 方法将 XML 文档或流读入数据集，使用 <xref:System.Data.DataSet.WriteXml%2A> 方法将数据集以 XML 格式写出。  因为 XML 是不同应用程序之间的标准数据交换格式，这意味着可以加载其他应用程序发送的包含 XML 格式信息的数据集。  同样，数据集可以将其数据集写出为 XML 流或文档，以与其他应用程序共享或只是将其存储为标准格式。  
  
-   可以创建数据集或数据表内容的 XML 视图（<xref:System.Xml.XmlDataDocument> 对象），然后用关系方法（通过数据集）或 XML 方法查看和操作数据。  这两种视图在更改时自动同步。  
  
## 类型化数据集与非类型化数据集  
 类型化数据集先是从基类 <xref:System.Data.DataSet> 派生，然后使用**“数据集设计器”**中的信息（存储在 .xsd 文件中）生成一个新的强类型数据集类。  架构中的信息（表、列等）被作为一组第一类对象和属性生成并编译为此新数据集类。  由于类型化数据集继承自基 <xref:System.Data.DataSet> 类，因此类型化类具有 <xref:System.Data.DataSet> 类的所有功能，可以与采用 <xref:System.Data.DataSet> 类的实例作为参数的方法一起使用。  
  
 相形之下，非类型化数据集没有相应的内置架构。  与类型化数据集一样，非类型化数据集也包含表、列等，但它们只作为集合公开。  （不过，在手动创建了非类型化数据集中的表和其他数据元素后，可以使用数据集的 <xref:System.Data.DataSet.WriteXmlSchema%2A> 方法将数据集的结构导出为一个架构。）  
  
### 对比类型化和非类型化数据集中的数据访问  
 类型化数据集的类有一个对象模型，在此对象模型中该类的属性采用表和列的实际名称。  例如，如果使用的是类型化数据集，可以使用如下代码引用列：  
  
 [!CODE [VbRaddataDatasets#4](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#4)]  
  
 相比较而言，如果使用的是非类型化数据集，等效的代码为：  
  
 [!CODE [VbRaddataDatasets#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataDatasets#5)]  
  
 类型化访问不但更易于读取，而且完全受 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**“代码编辑器”**中 IntelliSense 的支持。  除了更易于使用外，类型化数据集的语法还在编译时提供类型检查，从而大大降低了为数据集成员赋值时发生错误的可能性。  如果更改 <xref:System.Data.DataSet> 中的列名并编译应用程序，则会收到生成错误。  通过双击**“任务列表”**中的生成错误，可以直接转到引用旧列名的代码行。  在运行时对类型化数据集中的表和列的访问也略为快一些，因为访问是在编译时确定的，而不是在运行时通过集合确定。  
  
 尽管类型化数据集有许多优点，但在许多情况下需要使用非类型化数据集。  最显而易见的情形是数据集无架构可用。  例如，当应用程序正在与返回数据集的组件交互而您事先不知道其结构是哪种时，便会出现这种情况。  同样，有些时候使用的数据不具有静态的可预知结构，这种情况下使用类型化数据集是不切实际的做法，因为对于数据结构中的每个更改，您都必须重新生成类型化数据集类。  
  
 更常见的是，许多时候可能需要动态创建无可用架构的数据集。  这种情况下，数据集只是一种方便的、可用来保留信息的结构（只要数据可以用关系方法表示）。  同时，您还可以利用数据集的功能，如序列化传递到另一进程的信息或写出 XML 文件的能力。  
  
## 数据集的大小写敏感性  
 在数据集中，默认情况下表和列的名称不区分大小写，即数据集中名为“Customers”的表也可能是指“customers”。这符合包括 SQL Server 默认行为在内的许多数据库的命名约定，即数据元素的名称不能仅通过大小写区分。  
  
> [!NOTE]
>  与数据集不同，XML 文档是区分大小写的，因此架构中定义的数据元素的名称也区分大小写。  例如，架构协议允许架构定义一个名为“Customers”的表和另一个名为“customers”的不同的表。当使用架构生成数据集类时，如果该架构包含的元素仅存在大小写区别，这就会导致命名冲突。  
  
 不过，大小写敏感性可以成为决定数据在数据集中的解释方法的因素。  例如，在数据集表中筛选数据时，根据比较是否区分大小写，搜索判据可能返回不同的结果。  通过设置数据集的 <xref:System.Data.DataSet.CaseSensitive%2A> 属性，可以控制筛选、搜索和排序是否区分大小写。  默认情况下，数据集中的所有表都继承此属性的值。  （通过设置表的 <xref:System.Data.DataTable.CaseSensitive%2A> 属性，可以重写每个表的该属性。）  
  
## 相关表和 DataRelation 对象  
 如果数据集中有多个表，这些表中的信息可能是相关的。  数据集本身并不知道这样的关系；因此，若要使用相关表中的数据，可以创建 <xref:System.Data.DataRelation> 对象，这些对象描述了数据集中表之间的关系。  有关更多信息，请参见[如何：访问相关数据表中的记录](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)。  <xref:System.Data.DataRelation> 对象可用于以编程方式获取父记录的相关子记录，以及从子记录获取父记录。  有关更多信息，请参见[数据集中的关系](../data-tools/relationships-in-datasets.md)。  如果数据库包含两个或两个以上的表之间的关系，则设计工具将自动为您创建 <xref:System.Data.DataRelation> 对象。  
  
 例如，设想一下顾客和订单数据，如 Northwind 数据库中的情形。  `Customers` 表可能包含如下记录：  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 数据集也可能包含另一个含有订单信息的表。  `Orders` 表包含作为外键列的客户 ID。  只选择 `Orders` 表中的某些列，看起来可能类似于以下内容：  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 因为每个顾客可以有一个以上的订单，所以在顾客和订单之间存在一对多关系。  例如，在上表中，顾客 ALFKI 有两个订单。  
  
 可以用 <xref:System.Data.DataRelation> 对象从子表或父表获取相关记录。  例如，当使用描述顾客 ANTON 的记录时，可以获取描述该顾客的订单的记录集合。  有关更多信息，请参见 <xref:System.Data.DataRow.GetChildRows%2A>。  类似地，当使用描述 OrderId 10507 的记录时，可以向上定位关系对象以获取其父级 \(ANTON\) 的记录。  有关更多信息，请参见 <xref:System.Data.DataRow.GetParentRow%2A>。  
  
## 约束  
 与大多数数据库一样，数据集也支持约束，作为一种确保数据完整性的方法。  约束是在表中插入、更新或删除行时应用的规则。  可以定义两种类型的约束：  
  
-   *唯一*约束，检查列中的新值在表中是否是唯一的。  
  
-   *外键*约束，定义当主表中的记录被更新或删除时相关子记录应如何更新的规则。  例如，一个外键约束可以在允许创建任何子记录之前验证是否存在父记录。  
  
 在数据集中，约束与单个表（外键约束）或列（唯一约束，即保证列值具有唯一性的约束）关联。  约束作为类型 <xref:System.Data.UniqueConstraint> 或 <xref:System.Data.ForeignKeyConstraint> 的对象实现。  然后将其添加到 <xref:System.Data.DataTable> 的 <xref:System.Data.DataTable.Constraints%2A> 集合。  还可以通过简单地将 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataColumn.Unique%2A> 属性设置为 `true` 来指定唯一约束。  
  
 数据集本身支持布尔型的 <xref:System.Data.DataSet.EnforceConstraints%2A> 属性，该属性指定是否强制实施约束。  默认情况下，此属性设置为 `true`。  不过，有时暂时关闭约束很有用。  最常见的情形是当更改记录过程中所采用的方式将暂时导致无效状态时。  完成更改（并由此返回有效状态）后，可以重新启用约束。  
  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，定义数据集时会隐式创建约束。  通过将主键添加到数据集，即会为主键列隐式创建一个唯一约束。  通过将其他列的 <xref:System.Data.DataColumn.Unique%2A> 属性设置为 `true`，可以为它们指定唯一约束。  
  
 通过在数据集中创建 <xref:System.Data.DataRelation> 对象可以创建外键约束。  除了允许以编程方式获取有关相关记录的信息外，<xref:System.Data.DataRelation> 对象还允许定义外键约束规则。  
  
## 数据集扩展属性  
 当在从 .xsd 文件生成数据集的过程中遇到命名冲突时，扩展属性提供名称映射。  当 .xsd 文件中的标识符与数据集生成器创建的计算名称不同时，会有一个扩展属性被添加到 `msprop` 命名空间中的数据集。  下表列出了可生成的可能的扩展属性：  
  
|对象|扩展属性|  
|--------|----------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## 请参阅  
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio 的数据应用程序概述](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)