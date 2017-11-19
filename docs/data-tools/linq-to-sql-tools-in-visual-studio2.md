---
title: "Visual Studio O/R 设计器概述 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: cba3d5568ee2fa2b4af0eb9c10995c813fe09c01
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL Visual Studio 中的工具
LINQ to SQL 是 Microsoft 发布的第一个对象关系映射技术。 它适用于基本方案，并继续支持在 Visual Studio 中，但它不再进行活动开发。 使用 LINQ to SQL 时维护的旧应用程序已在使用它，或简单的应用程序使用 SQL Server 并不需要多表映射。 一般情况下，新的应用程序应使用实体框架时是必需的对象关系映射器层。  
  
在 Visual Studio 中，你创建 LINQ to SQL 类表示通过使用对象关系设计器 （O/R 设计器） 的 SQL 表。  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]具有其设计图面上的两个不同的区域： 实体窗格左侧和右侧的方法窗格。 实体窗格是主设计图面，其中显示实体类、关联和继承层次结构。 方法窗格是显示映射到存储过程和函数的 <xref:System.Data.Linq.DataContext> 方法的设计图面。  
  
[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供用于创建可视化设计图面[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)实体类和关联 （关系） 基于数据库中的对象。 换句话说，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]用于在应用程序中创建映射到数据库中的对象的对象模型。 它还生成一个强类型 <xref:System.Data.Linq.DataContext>，用于在实体类与数据库之间发送和接收数据。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]还提供了相关功能，用于将存储过程和函数映射到 <xref:System.Data.Linq.DataContext> 方法以便返回数据和填充实体类。 最后，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供了对实体类之间的继承关系进行设计的能力。  
  
## <a name="opening-the-or-designer"></a>打开 O/R 设计器  
 若要添加 LINQ to SQL 实体模型到你的项目，选择**项目**，**添加新项**，然后选择**LINQ to SQL 类**从项目项的列表：  
  
 ![LINQ to SQL 类](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL 类")  
  
 Visual Studio 创建一个.dbml 文件，并将其添加到你的解决方案。 这是 XML 映射文件和其相关的代码文件。  
  
 ![在解决方案资源管理器中的 LINQ to SQL 类](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL 类在解决方案资源管理器")  
  
 当你选择的.dbml 文件时，Visual Studio 将显示可用于以可视方式创建模型 O/R 设计器图面。 从服务器资源管理器中拖动到 Northwind Customers 和 Orders 表后下, 图显示设计器。 请注意表之间的关系。  
  
 ![到 SQL 设计器的 LINQ](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL 设计器")  
  
> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]是一个简单的对象关系映射器，因为它仅支持 1:1 映射关系。 换句话说，实体类与数据库表或视图之间只能具有 1:1 映射关系。 不支持复杂映射，如将实体类映射到联接表;使用实体框架进行复杂映射。 此外，该设计器还是一个单向代码生成器。 这表示代码文件中只反映对设计器图面所做的更改。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中不会反映对代码文件的手动更改。 在保存设计器并重新生成代码时，将覆盖在代码文件中手动进行的所有更改。 有关如何添加用户代码和扩展由生成的类信息[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，请参阅[如何： 扩展 O/R 设计器生成代码](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)。  
  
## <a name="creating-and-configuring-the-datacontext"></a>创建和配置 DataContext  
 添加后**LINQ to SQL 类**项目到项目，然后打开[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，空设计图面表示一个空<xref:System.Data.Linq.DataContext>可供配置。 <xref:System.Data.Linq.DataContext>配置通过拖动到设计图面上的第一项提供的连接信息... 因此，<xref:System.Data.Linq.DataContext> 是使用放置到设计图面上的第一项中的连接信息进行配置的。 有关详细信息<xref:System.Data.Linq.DataContext>类，请参阅[DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>创建映射到数据库表和视图的实体类  
 你可以创建实体类映射到表和视图，通过拖动数据库表和视图从**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 正如上一节中所述，<xref:System.Data.Linq.DataContext> 是使用拖动到设计图面上的第一项所提供的连接信息进行配置的。 如果将一个使用不同连接的后续项添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中，您可以更改 <xref:System.Data.Linq.DataContext> 的连接。 有关详细信息，请参阅[如何： 创建 LINQ to SQL 类映射到表和视图 （O/R 设计器）](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)。  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>创建调用存储过程和函数的 DataContext 方法  
 你可以创建<xref:System.Data.Linq.DataContext>调用的方法 （映射到中） 通过将其从拖动存储过程和函数**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. 存储过程和函数作为 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 的方法添加到 <xref:System.Data.Linq.DataContext>中。  
  
> [!NOTE]
>  将存储的过程和函数从**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，生成的返回类型<xref:System.Data.Linq.DataContext>方法不同具体取决于放置项的位置。 有关详细信息，请参阅[DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>配置 DataContext 以使用存储过程来保存实体类和数据库之间的数据  
 如上文所述，您可以创建调用存储过程和函数的 <xref:System.Data.Linq.DataContext> 方法。 此外，您还可以分配执行插入、更新和删除操作的默认 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 运行时行为可以使用的存储过程。 有关详细信息，请参阅[如何： 分配存储的过程以便执行更新、 插入和删除操作 （O/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)。  
  
## <a name="inheritance-and-the-or-designer"></a>继承和 O/R 设计器  
 像其他对象一样，[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 类可以使用继承，并可从其他类派生。 在数据库中，可通过多种方式创建继承关系。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]支持通常在关系系统中实现的单表继承概念。 有关详细信息，请参阅[如何： 通过使用 O/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)。  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL 查询  
 创建的实体类[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]专用于[LINQ （语言集成查询）](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)。 有关详细信息，请参阅[如何： 查询有关的信息](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)。  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>将生成的 DataContext 和实体类代码分离到不同的命名空间  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]提供**上下文 Namespace**和**实体 Namespace**属性<xref:System.Data.Linq.DataContext>。 这些属性决定 <xref:System.Data.Linq.DataContext> 和实体类代码生成到哪个命名空间。 默认情况下，这些属性为空并且 <xref:System.Data.Linq.DataContext> 和实体类生成到应用程序的命名空间。 若要生成应用程序的命名空间之外的命名空间中的代码，请输入值转换为**上下文 Namespace**和/或**实体 Namespace**属性。
  
## <a name="reference-content"></a>参考内容
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>请参阅
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[Frequently Asked Questions (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 