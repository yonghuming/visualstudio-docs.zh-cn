---
title: "如何： 通过使用 O R 设计器配置继承 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8b4c2ac7790bd2c5114b04a6119702013d54825b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>如何： 通过使用 O/R 设计器配置继承
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]（[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]）支持通常在关系系统中实现的单表继承概念。 在单表继承中，一个数据库表同时包含父信息和子信息的字段。 使用关系数据时，一个鉴别器列包含的值确定任意记录属于哪个类。  
  
例如，考虑一个包含公司所有员工的 Persons 表。 一些人是员工，一些人是经理。 Persons 表包含一个名为 `EmployeeType` 的列，其中值 1 表示经理，值 2 表示员工。这个列就是鉴别器列。 在此应用场景中，可以创建一个员工子类，并仅使用 `EmployeeType` 值为 2 的记录来填充该类。 还可以从每个类中移除不适用的列。  
  
创建一个使用继承（并对应于关系数据）的对象模型可能有些不易理解。 下面的过程概括说明使用 O/R 设计器配置继承所需的步骤。 如果不对照现有的表和列实际操作，则可能很难理解和掌握一般性的操作步骤，因此我们提供了一个使用数据的演练。 有关详细的分步指导，通过使用配置继承[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，请参阅[演练： 创建 LINQ to SQL 类通过使用单表继承 （O/R 设计器）](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)。  
  
## <a name="to-create-inherited-data-classes"></a>创建继承的数据类
  
1.  打开[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]通过添加**LINQ to SQL 类**到现有 Visual Basic 或 C# 项目的项。  
  
2.  将要用作基类的表拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上。  
  
3.  将该表的第二个副本拖到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]上并重命名该副本。 这是派生类，即子类。  
  
4.  单击**继承**中**对象关系设计器**选项卡**工具箱**，然后单击子类 （重命名的表） 并将其连接到的基类。  
  
    > [!NOTE]
    >  单击**继承**中项**工具箱**和释放鼠标按钮单击步骤 3 中创建的类的第二个副本，然后单击你在步骤 2 中创建的第一个类。 继承连线中的箭头将指向第一个类。  
  
5.  在每个类中，删除任何不希望显示和没有用于关联的对象属性。 如果你尝试删除用于关联的对象属性，将收到一个错误：[属性\<属性名称 > 无法删除，因为它参与关联\<关联名称 >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  由于派生类继承其基类中定义的属性，在每个类中不能定义相同的列。 （列实现为属性。）通过设置基类属性中的继承修饰符，可以在派生类中创建列。 有关详细信息，请参阅[继承的基础知识 (Visual Basic 中)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)。  
  
6.  在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中选择继承连线。  
  
7.  在**属性**窗口中，设置**鉴别器属性**为用于区分您的类中的记录的列名称。  
  
8.  设置**派生类鉴别器值**属性中的数据库，将记录指定为继承的类型的值。 （这是存储在鉴别器列中的值，用于指定继承的类。）  
  
9. 设置**基类鉴别器值**将记录指定为基类型的值的属性。 （这是存储在鉴别器列中的值，用于指定基类。）  
  
10. （可选） 还可以设置**继承默认值**属性，以便指定在加载与任何不匹配的行定义的继承代码时使用的继承层次结构中的类型。 换而言之，如果记录在其鉴别器列中的值不匹配的值中任意一种**派生类鉴别器值**或**基类鉴别器值**属性，则请记录将加载到指定为的类型**继承默认值**。  
  
## <a name="see-also"></a>请参阅
[LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[演练： 创建 LINQ to SQL 类 （O R 设计器）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[PAVE Visual Studio 2012 中的数据应用程序开发的新增功能](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
[在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[演练： 使用单表继承 （O/R 设计器） 创建 LINQ to SQL 类](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
[继承的基础知识 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)  
[继承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)