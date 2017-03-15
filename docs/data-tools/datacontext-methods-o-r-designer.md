---
title: "DataContext 方法（O/R 设计器） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DataContext 方法（O/R 设计器）
<xref:System.Data.Linq.DataContext> 方法（在[对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)上下文中）是 <xref:System.Data.Linq.DataContext> 类的方法，这些方法运行数据库中的存储过程和函数。  
  
 <xref:System.Data.Linq.DataContext> 类是一个 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类，它充当 SQL Server 数据库与映射到该数据库的 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 实体类之间的管道。<xref:System.Data.Linq.DataContext> 类包含用于连接数据库以及操作数据库数据的连接字符串信息和方法。默认情况下，<xref:System.Data.Linq.DataContext> 类包含多个可以调用的方法，例如用于将已更新数据从 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类发送到数据库的 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 方法。还可以创建其他映射到存储过程和函数的 <xref:System.Data.Linq.DataContext> 方法。也就是说，调用这些自定义方法将运行数据库中 <xref:System.Data.Linq.DataContext> 方法所映射到的存储过程或函数。和可以添加方法对任何类进行扩展一样，您也可以将新方法添加到 <xref:System.Data.Linq.DataContext> 类。但是，在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的上下文中讨论 <xref:System.Data.Linq.DataContext> 方法时，讨论的是映射到存储过程和函数的 <xref:System.Data.Linq.DataContext> 方法。  
  
> [!NOTE]
>  在 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中，存储过程和函数的处理方式相同，因为它们使用同一 <xref:System.Data.Linq.StoredProcedureAttribute> 映射到实体类。在 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 的上下文中，映射到存储过程的 <xref:System.Data.Linq.DataContext> 方法和映射到函数的方法相同。  
  
## 方法窗格  
 映射到存储过程和函数的 <xref:System.Data.Linq.DataContext> 方法显示在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]的方法窗格中。方法窗格位于**“实体”**窗格（主设计图面）的旁边。方法窗格列出使用 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]创建的所有 <xref:System.Data.Linq.DataContext> 方法。默认情况下，方法窗格是空的；将存储过程或函数从**“服务器资源管理器”**\/**“数据库资源管理器”**拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上将创建 <xref:System.Data.Linq.DataContext> 方法并填充方法窗格。有关更多信息，请参见[如何：创建映射到存储过程和函数的 DataContext 方法（O\/R 设计器）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)。  
  
> [!NOTE]
>  通过右击 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]然后单击**“隐藏方法窗格”**或**“显示方法窗格”**，或者使用键盘快捷键 Ctrl\+1，可以打开和关闭方法窗格。  
  
## DataContext 方法的两种类型  
 DataContext 方法指的是那些映射到数据库中的存储过程和函数的方法。您可以在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 的方法窗格上创建并添加 DataContext 方法。有两种不同类型的 <xref:System.Data.Linq.DataContext> 方法；一种会返回一个或多个结果集，而另一种则不会：  
  
-   返回一个或多个结果集的 <xref:System.Data.Linq.DataContext> 方法：  
  
     如果应用程序只需运行数据库中的存储过程和函数并返回结果，可创建这种 <xref:System.Data.Linq.DataContext> 方法。有关更多信息，请参见 [如何：创建映射到存储过程和函数的 DataContext 方法（O\/R 设计器）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)、<xref:System.Data.Linq.ISingleResult%271> 和 <xref:System.Data.Linq.IMultipleResults>。  
  
-   不返回结果集的 <xref:System.Data.Linq.DataContext> 方法，例如：对特定实体类执行插入、更新和删除操作。  
  
     如果应用程序需要运行存储过程而不是使用默认 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 行为来保存实体类和数据库之间修改的数据，可创建这种 <xref:System.Data.Linq.DataContext> 方法。有关更多信息，请参见[如何：分配存储过程以执行更新、插入和删除（O\/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## DataContext 方法的返回类型  
 将存储过程和函数从**“服务器资源管理器”**\/**“数据库资源管理器”**拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上时，生成的 <xref:System.Data.Linq.DataContext> 方法的返回类型取决于项的放置位置。如果直接将项放在现有实体类上，则将创建具有该实体类返回类型的 <xref:System.Data.Linq.DataContext> 方法；如果将项放在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]（任一窗格）的空白区域，则将创建返回自动生成类型的 <xref:System.Data.Linq.DataContext> 方法。创建的自动生成类型的名称与存储过程或函数名称匹配，属性映射到存储过程或函数返回的字段。  
  
> [!NOTE]
>  在将 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格后可以更改该方法的返回类型。若要检查或更改 <xref:System.Data.Linq.DataContext> 方法的返回类型，请选中该方法并在**“属性”**窗口中检查**“返回类型”**属性。有关更多信息，请参见[如何：更改 DataContext 方法的返回类型（O\/R 设计器）](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)。  
  
 从数据库拖动到 O\/R 设计器图面上的对象将根据数据库中的对象的名称自动命名。如果您多次拖动同一个对象，将会在新名称的末尾追加一个数字来区别名称。如果数据库对象名称包含空格或 Visual Basic 或 C\# 中不支持的字符，将使用下划线替代空格或无效字符。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [存储过程](../Topic/Stored%20Procedures.md)   
 [如何：创建映射到存储过程和函数的 DataContext 方法（O\/R 设计器）](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [如何：分配存储过程以执行更新、插入和删除（O\/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [演练：自定义实体类的插入、更新和删除行为](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)