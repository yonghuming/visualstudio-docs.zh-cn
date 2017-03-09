---
title: "LINQ to SQL 工具 Visual Studio2 中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to SQL 工具在 Visual Studio 中
LINQ to SQL 是由 Microsoft 发布的第一个对象关系映射技术。 它适用于基本方案，并继续在 Visual Studio 中受到支持，但它不再处于活动状态的开发。 使用 LINQ to SQL 时维护旧版应用程序已在使用它，或使用 SQL Server 并不需要多表映射的简单应用程序。 一般情况下，新的应用程序应使用实体框架时是必需的对象关系映射器图层。  
  
 在 Visual Studio 中创建 LINQ to SQL 类表示使用的 SQL 表 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 有其设计图面上两个不同的区域︰ 左侧的实体窗格和右侧的方法窗格。 实体窗格是主设计图面，其中显示实体类、关联和继承层次结构。 方法窗格是显示设计图面 <xref:System.Data.Linq.DataContext> 映射到存储的过程和函数的方法。  
  
  [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) 提供了可视化设计图面创建 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) 实体类和关联 （关系），基于数据库中的对象。 换句话说，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]用于在应用程序中创建映射到数据库中的对象的对象模型。 它还生成一个强类型 <xref:System.Data.Linq.DataContext> 用于发送和接收的实体类与数据库之间的数据。  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 还提供了功能来映射存储的过程和函数 <xref:System.Data.Linq.DataContext> 方法以便返回数据和填充实体类。 最后，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供了对实体类之间的继承关系进行设计的能力。  
  
## <a name="opening-the-or-designer"></a>打开 O/R 设计器  
 若要添加一个 LINQ to SQL 实体模型到你的项目，选择 **项目 &#124;添加新项** ，然后选择  **LINQ to SQL 类** 从项目项的列表︰  
  
 ![LINQ to SQL 类](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio 创建一个.dbml 文件，并将其添加到您的解决方案。 这是 XML 映射文件和其相关的代码文件。  
  
 ![LINQ to SQL 类在解决方案资源管理器](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 当选中此.dbml 文件时，Visual Studio 将显示该对话框可直观地创建模型 O/R 设计器图面。 下图显示的设计器后从服务器资源管理器中拖动到 Northwind Customers 和 Orders 表。 请注意在表之间的关系。  
  
 ![LINQ to SQL 设计器](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  
          [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]是一个简单的对象关系映射器，因为它仅支持 1:1 映射关系。 换句话说，实体类与数据库表或视图之间只能具有 1:1 映射关系。 不支持复杂映射，如将实体类映射到联接表;使用实体框架进行复杂的映射。 此外，该设计器还是一个单向代码生成器。 这表示代码文件中只反映对设计器图面所做的更改。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中不会反映对代码文件的手动更改。 在保存设计器并重新生成代码时，将覆盖在代码文件中手动进行的所有更改。 有关如何添加用户代码和扩展生成的类信息 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], ，请参阅 [如何︰ 扩展 O/R 设计器生成代码](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)。  
  
## <a name="creating-and-configuring-the-datacontext"></a>创建和配置 DataContext  
 在添加后 **LINQ to SQL 类** 项目到项目，然后打开 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], ，空设计图面表示一个空 <xref:System.Data.Linq.DataContext> 可对其进行配置。  <xref:System.Data.Linq.DataContext> 使用拖动到设计图面上的第一项提供的连接信息进行配置... 因此， <xref:System.Data.Linq.DataContext> 通过拖放到设计图面上面的第一个项中的连接信息进行配置。 有关详细信息 <xref:System.Data.Linq.DataContext> 类，请参阅 [DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>创建映射到数据库表和视图的实体类  
 您可以创建实体类映射到表和视图通过将数据库表和视图从 **服务器资源管理器**/**数据库资源管理器** 拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 上一节中所示 <xref:System.Data.Linq.DataContext> 使用拖动到设计图面上的第一项提供的连接信息进行配置。 如果使用不同的连接的后续项添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], ，可以更改用于连接 <xref:System.Data.Linq.DataContext>。 有关详细信息，请参阅 [如何︰ 创建 LINQ to SQL 类映射到表和视图 （O/R 设计器）](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)。  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>创建调用存储过程和函数的 DataContext 方法  
 您可以创建 <xref:System.Data.Linq.DataContext> 调用的方法 （映射到中） 存储过程和函数，通过将其从拖动 **服务器资源管理器**/**数据库资源管理器** 拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 存储的过程和函数添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 作为方法的 <xref:System.Data.Linq.DataContext>。  
  
> [!NOTE]
>  当您将存储的过程和函数从 **服务器资源管理器**/**数据库资源管理器** 拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], ，生成的返回类型 <xref:System.Data.Linq.DataContext> 方法不同，具体取决于放置项的位置。 有关详细信息，请参阅 [DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>配置 DataContext 以使用存储过程来保存实体类和数据库之间的数据  
 正如前文所述，您可以创建 <xref:System.Data.Linq.DataContext> 调用存储的过程和函数的方法。 此外，您还可以分配执行插入、更新和删除操作的默认 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时行为可以使用的存储过程。 有关详细信息，请参阅 [如何︰ 分配存储的过程以便执行更新、 插入和删除操作 （O/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## <a name="inheritance-and-the-or-designer"></a>继承和 O/R 设计器  
 像其他对象一样，[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类可以使用继承，并可从其他类派生。 在数据库中，可通过多种方式创建继承关系。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]支持通常在关系系统中实现的单表继承概念。 有关详细信息，请参阅 [如何︰ 通过使用 O/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL 查询  
 创建的实体类 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 专用于 [LINQ （语言集成查询）](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。 有关详细信息，请参阅 [如何︰ 查询有关的信息](../Topic/How%20to:%20Query%20for%20Information.md)。  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>将生成的 DataContext 和实体类代码分离到不同的命名空间  
  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 提供 **上下文 Namespace** 和 **实体 Namespace** 属性 <xref:System.Data.Linq.DataContext>。 这些属性确定哪个命名空间 <xref:System.Data.Linq.DataContext> 和实体类代码生成到。 默认情况下，这些属性为空并且 <xref:System.Data.Linq.DataContext> 和实体类生成到应用程序的命名空间。 若要生成应用程序的命名空间之外的命名空间中的代码，请输入一个值 **上下文 Namespace** 和/或 **实体 Namespace** 属性。  
  
## <a name="in-this-section"></a>本节内容  
 [DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)  
 解释什么是 <xref:System.Data.Linq.DataContext> 方法，以及如何创建它们。  
  
 [数据类继承 （O/R 设计器）](../data-tools/data-class-inheritance-o-r-designer.md)  
 描述单表继承的概念以及如何在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中实现这种继承。  
  
 [如何︰ 创建 LINQ to SQL 类映射到表和视图 （O/R 设计器）](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)  
 描述如何创建映射到数据库中表和视图的实体类。  
  
 [如何︰ 创建 LINQ to SQL 类 （O/R 设计器） 之间的关联 （关系）](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 描述如何创建 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 实体类之间的关系。  
  
 [如何︰ 创建映射到存储的过程和函数 （O/R 设计器） 的 DataContext 方法](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 描述如何创建 <xref:System.Data.Linq.DataContext> 在被调用时运行存储的过程或函数的方法。  
  
 [如何︰ 分配存储的过程以便执行更新、 插入和删除操作 （O/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 描述如何配置 <xref:System.Data.Linq.DataContext> 时要使用存储的过程将数据保存从实体类回数据库。  
  
 [如何︰ 更改 DataContext 方法 （O/R 设计器） 的返回类型](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 描述如何设置的返回类型 <xref:System.Data.Linq.DataContext> 方法视为一个实体类的类型或由 O/R 设计器创建的自动生成类型。  
  
 [如何︰ 向实体类添加验证](../data-tools/how-to-add-validation-to-entity-classes.md)  
 描述如何生成分部方法，以便能够在属性更改或实体类更新过程中添加代码。  
  
 [如何︰ 将复数形式打开和关闭 （O/R 设计器）](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 描述如何打开和关闭添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中的类的自动重命名功能。  
  
 [如何︰ 通过使用 O/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 描述如何通过 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]使用单表继承配置实体类。  
  
 [如何︰ 扩展 O/R 设计器生成的代码](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)  
 描述如何添加以及在何处添加在对 O/R 设计器中的对象所做的更改重新生成代码时不会被覆盖的代码。  
  
 [演练︰ 创建 LINQ to SQL 类通过使用单表继承 （O/R 设计器）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 提供有关通过 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]使用单表继承配置实体类的分步说明。  
  
 [演练︰ 自定义插入、 更新和删除的实体类的行为](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 提供有关配置的分步说明 <xref:System.Data.Linq.DataContext> 时要使用存储的过程将数据保存从实体类回数据库。  
  
## <a name="reference-content"></a>参考内容  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>另请参阅  
 [适用于.NET 的 visual Studio data tools](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [常见问题](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)