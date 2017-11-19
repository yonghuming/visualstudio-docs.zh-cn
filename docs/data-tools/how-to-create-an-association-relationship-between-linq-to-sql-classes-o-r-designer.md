---
title: "如何创建 LINQ to SQL 类使用 O/R 设计器之间的关系关系 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: dff1251824a07e8448c6f0dbcf421776d90977a2
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>如何： 创建 LINQ to SQL 类 （O/R 设计器） 之间的关联
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 中实体类之间的关联类似于数据库中表之间的关系。 你可以创建使用的实体类之间的关联**关联编辑器**对话框。  
  
使用时，您必须选择父类和子类**关联编辑器**对话框创建关联。 父类是包含主键的实体类；子类是包含外键的实体类。 例如，如果创建映射到 Northwind Customers 和 Orders 表的实体类，则 Customer 类将是父类，而 Order 类将是子类。  
  
> [!NOTE]
>  将表从**服务器资源管理器**/**数据库资源管理器**到[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)])，将自动创建基于现有关联数据库中的外键关系。  

## <a name="association-properties"></a>关联属性
当您在 O/R 设计器中选择该关联时创建关联之后，有一些可配置属性中的**属性**窗口。 （关联是用相关类之间的连线表示的。）下表提供对关联的属性的说明。  
  
|属性|描述|  
|--------------|-----------------|  
|**基数**|控制关联是一对多关系还是一对一关系。|  
|**子属性**|指定是否在父类上创建一个属性，作为关联关系外键一方上的子记录的集合或对这些子记录的引用。 例如，在 Customer 和 Order，之间的关联如果**子属性**设置为**True**，父类上创建名为 Orders 的属性。|  
|**父属性**|子类上引用关联父类的属性。 例如，在 Customer 和 Order 之间的关联中，在 Order 类上创建一个名为 Customer 的属性，用来引用与订单关联的客户。|  
|**参与属性**|显示关联属性，并提供**省略号**按钮 （…），用于重新打开**关联编辑器**对话框。|  
|**唯一**|指定外目标列是否具有唯一性约束。|  
  
## <a name="to-create-an-association-between-entity-classes"></a>创建实体类之间的关联
  
1.  右击表示关联中的父类的实体类，指向**添加**，然后单击**关联**。  
  
2.  确认正确**父类**中选择**关联编辑器**对话框。  
  
3.  选择**子类**组合框中。  
  
4.  选择**关联属性**类之间。 通常，这种关联对应于数据库中定义的外键关系。 例如，在 Customers 和 Orders 关联中，**关联属性**是为每个类的 CustomerID。  
  
5.  单击**确定**创建关联。  
  
## <a name="see-also"></a>请参阅
[LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[演练： 创建 LINQ to SQL 类](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[DataContext 方法 （O/R 设计器）](../data-tools/datacontext-methods-o-r-designer.md)   
[如何： 表示主键](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)