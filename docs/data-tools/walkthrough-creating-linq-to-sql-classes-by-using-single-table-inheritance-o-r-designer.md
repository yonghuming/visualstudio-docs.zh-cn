---
title: "演练： 使用单表继承 （O R 设计器） 创建 LINQ to SQL 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: a6794fb327e298aa8fa7ea313ff12e1b3ab99fb9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>演练：通过使用单表继承创建 LINQ to SQL 类（O/R 设计器）
[LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)支持单表继承，因为它通常在关系系统中实现。 本演练中提供的一般步骤进行了扩展[如何： 通过使用 O/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)主题，并提供演示如何使用中的继承某些实际数据[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
 在本演练中，你将要执行以下任务：  
  
-   创建一个数据库表，并向其中添加数据。  
  
-   创建一个 Windows 窗体应用程序。  
  
-   将一个 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 文件添加到项目。  
  
-   创建新的实体类。  
  
-   配置实体类使用继承。  
  
-   查询继承类。  
  
-   在 Windows 窗体上显示数据。  
  
## <a name="create-a-table-to-inherit-from"></a>创建要从中继承的表  
 为了解继承的工作方式，您将创建一个小的 Person 表用作基类，然后创建一个从该表继承的 Employee 对象。  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>创建基表以演示继承  
  
1.  在**服务器资源管理器**/**数据库资源管理器**，右键单击**表**节点，然后单击**添加新表**。  
  
    > [!NOTE]
    >  可以使用 Northwind 数据库或其他任何可添加表的数据库。  
  
2.  在表设计器中，向该表中添加以下列：  
  
    |列名|数据类型|允许为 Null|  
    |-----------------|---------------|-----------------|  
    |**ID**|**int**|**False**|  
    |**类型**|**int**|**True**|  
    |**FirstName**|**nvarchar （200)**|**False**|  
    |**LastName**|**nvarchar （200)**|**False**|  
    |**管理器**|**int**|**True**|  
  
3.  将 ID 列设置为主键。  
  
4.  保存该表并将其命名**人员**。  
  
## <a name="add-data-to-the-table"></a>向表中添加数据  
 为了验证对继承的配置是否正确，表对于单表继承中的每个类都需要一些数据。  
  
#### <a name="to-add-data-to-the-table"></a>向表中添加数据。  
  
1.  在数据视图中打开该表。 (右键单击**人员**表中**服务器资源管理器**/**数据库资源管理器**单击**显示表数据**。)  
  
2.  将下面的数据复制到表中。 （你可以将其复制，然后，通过在结果窗格中选择整个行，将其粘贴到表。）  
  
    ||||||  
    |-|-|-|-|-|  
    |**ID**|**类型**|**FirstName**|**LastName**|**管理器**|  
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|  
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|  
    |**3**|**1**|**Yael**|**Peled**|**NULL**|  
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|  
    |**5**|**2**|**Andreas**|**Hauser**|**1**|  
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|  
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|  
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|  
    |**9**|**2**|**尾部**|**Yee**|**2**|  
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|  
    |**11**|**2**|**我**|**Martin**|**3**|  
    |**12**|**2**|**Ken**|**Kwok**|**3**|  
  
## <a name="create-a-new-project"></a>创建新项目  
 至此，表已经创建完毕，下面创建一个新项目演示对继承的配置。  
  
#### <a name="to-create-the-new-windows-forms-application"></a>若要创建新的 Windows 窗体应用程序  
  
1. 在 Visual Studio 中，在**文件**菜单上，选择**新建**，**项目...**.  
  
2. 展开**Visual C#**或**Visual Basic**在左侧窗格中，然后选择**Windows 经典桌面**。  

3. 在中间窗格中，选择**Windows 窗体应用程序**项目类型。  

4. 将项目**命名为 InheritanceWalkthrough**，然后选择**确定**。 
  
     **命名为 InheritanceWalkthrough**项目时创建，并添加到**解决方案资源管理器**。  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>将 LINQ to SQL 类文件添加到项目  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>将 LINQ to SQL 文件添加到项目  
  
1.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
2.  单击**LINQ to SQL 类**模板，然后单击**添加**。  
  
     .dbml 文件即添加到项目，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]打开。  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>使用 O/R 设计器创建继承  
 通过拖动来配置继承**继承**对象**工具箱**拖到设计图面。  
  
#### <a name="to-create-the-inheritance"></a>创建继承  
  
1.  在**服务器资源管理器**/**数据库资源管理器**，导航到**人员**前面创建的表。  
  
2.  拖动**人员**表拖动到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]设计图面。  
  
3.  将另一个**人员**表拖动到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]和其将名称更改为**员工**。  
  
4.  删除**Manager**属性从**人员**对象。  
  
5.  删除**类型**， **ID**， **FirstName**，和**LastName**属性从**员工**对象。 (在换而言之，删除以外的所有属性**Manager**。)  
  
6.  从**对象关系设计器**选项卡**工具箱**，创建**继承**之间**人员**和**员工**对象。 若要执行此操作，请单击**继承**中项**工具箱**和释放鼠标按钮。 接下来，单击**员工**对象，然后**人员**对象在[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。 继承连线上的箭头将指向**人员**对象。  
  
7.  单击**继承**设计图面上的行。  
  
8.  设置**鉴别器属性**属性**类型**。  
  
9. 设置**派生类鉴别器值**属性**2**。  
  
10. 设置**基类鉴别器值**属性**1**。  
  
11. 设置**继承默认值**属性**人员**。  
  
12. 生成项目。  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>查询继承类并在窗体上显示数据  
 您将向窗体中添加一些代码，用于在对象模型中查询特定的类。  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>创建一个 LINQ 查询并在窗体上显示结果  
  
1.  拖动**ListBox**拖到 Form1 上。  
  
2.  双击窗体以创建 `Form1_Load` 事件处理程序。  
  
3.  将以下代码添加到 `Form1_Load` 事件处理程序中：  
  
    ```vb  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```csharp  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## <a name="test-the-application"></a>测试应用程序  
 运行应用程序并检验列表框中显示的记录是否全为员工（“Type”列值为 2 的记录）。  
  
#### <a name="to-test-the-application"></a>测试应用程序  
  
1.  按 F5。  
  
2.  检验是否仅显示了“Type”列值为 2 的记录。  
  
3.  关闭窗体。 (在**调试**菜单上，单击**停止调试**。)  
  
## <a name="see-also"></a>另请参阅  
 [LINQ to SQL Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [演练： 创建 LINQ to SQL 类 （O R 设计器）](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [如何： 分配存储的过程以便执行更新、 插入和删除操作 （O/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [如何： 在 Visual Basic 或 C# 中生成的对象模型](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)