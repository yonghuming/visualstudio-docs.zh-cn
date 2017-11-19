---
title: "使用存储过程以便执行更新、 插入、 和 Linq to SQL O/R 设计器中删除 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f0d6910d2bf449172bac86a3ecd18be8169ef244
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>如何： 分配存储的过程以便执行更新、 插入和删除操作 （O/R 设计器）
可以将存储过程添加到 O/R 设计器并作为典型的 <xref:System.Data.Linq.DataContext> 方法执行。 将更改从实体类保存到数据库时（例如在调用 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 方法时），还可以使用存储过程重写执行插入、更新和删除操作的默认 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 运行时行为。  
  
> [!NOTE]
>  如果存储过程的返回值需要发送回客户端（例如在存储过程中计算出的值），则在存储过程中创建输出参数。 如果无法使用输出参数，则编写分部方法实现，而不是依靠 O/R 设计器生成的重写。 在成功完成 INSERT 或 UPDATE 操作后，需要将映射到数据库生成的值的成员设置为相应的值。 有关详细信息，请参阅[开发人员在重写默认行为中的责任](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 会自动为标识（自动递增）列、rowguidcol（数据库生成的 GUID）列和时间戳列处理数据库生成的值。 在其他列类型中，数据库生成的值将意外导致 Null 值。 若要返回数据库生成的值，应手动将 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 设置为 `true` 并将 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> 设置为下列值之一：<xref:System.Data.Linq.Mapping.AutoSync>、<xref:System.Data.Linq.Mapping.AutoSync> 或 <xref:System.Data.Linq.Mapping.AutoSync>。  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>配置实体类的更新行为  
 默认情况下，若要对中的数据所做的更改更新数据库 （插入、 更新和删除） 的逻辑[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]实体类提供的[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]运行时。 运行时创建默认基于的 INSERT、 UPDATE 和 DELETE 命令表 （列和主键信息） 的架构。 时不需要默认行为，你可以通过分配特定的存储的过程执行必需的插入、 更新和删除操作表中的数据所需的配置更新行为。 在不生成默认行为时（例如，实体类映射到视图时），也可以这样做。 最后，在数据库要求通过存储过程访问表时，您可以重写默认的更新行为。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>指定存储过程以重写实体类的默认行为  
  
1.  打开**LINQ to SQL**设计器中的文件。 (双击中的.dbml 文件**解决方案资源管理器**。)  
  
2.  在**服务器资源管理器**/**数据库资源管理器**，展开**存储过程**，找到你想要用于插入、 更新、 存储的过程和/或 Delete 命令的实体类。  
  
3.  将该存储过程拖到 O/R 设计器上。  
  
     该存储过程将作为 <xref:System.Data.Linq.DataContext> 方法添加到方法窗格中。 有关详细信息，请参阅[DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)。  
  
4.  选择要使用存储过程对其执行更新的实体类。  
  
5.  在**属性**窗口中，选择要重写的命令 (**插入**，**更新**，或**删除**)。  
  
6.  单击旁边的省略号 （...）**使用运行时**以打开**配置行为**对话框。  
  
7.  选择**自定义**。  
  
8.  选择所需的存储的过程中**自定义**列表。  
  
9. 检查的列表**方法自变量**和**类属性**以便确认**方法自变量**映射到相应**类属性**. 映射原始方法自变量 (Original_*ArgumentName*) 到原始属性 (*PropertyName* （原始）) 为 Update 和 Delete 命令。  
  
    > [!NOTE]
    >  默认情况下，名称匹配时方法自变量映射到类属性。 如果更改的属性名称在表和实体类之间不再匹配，而设计器无法确定正确的映射，您可能需要选择等效的类属性进行映射。  
  
10. 单击**确定**或**应用**。  
  
    > [!NOTE]
    >  你可以继续配置为每个类/行为组合的行为，只要你单击**应用**每次更改后。 如果你更改类或行为之前单击**应用**、 提供机会应用任何更改将出现一个警告对话框。  
  
若要恢复为默认运行时逻辑用于更新，请单击 Insert、 Update、 旁边的省略号或删除命令中的**属性**窗口，然后选择**使用运行时**中**配置行为**对话框。  
  
## <a name="see-also"></a>请参阅
[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[DataContext 方法](../data-tools/datacontext-methods-o-r-designer.md)   
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)   
[插入、 更新和删除操作 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)