---
title: "演练：使用单表继承创建 LINQ to SQL 类（O/R 设计器） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：使用单表继承创建 LINQ to SQL 类（O/R 设计器）
[对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)支持通常在关系系统中实现的单表继承。此演练对[如何：使用 O\/R 设计器配置继承](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)主题中提供的通用步骤进行了扩展，提供一些真实数据演示在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中对继承的使用。  
  
 在本演练中，您将要执行以下任务：  
  
-   创建一个数据库表，并向其中添加数据。  
  
-   创建一个 Windows 窗体应用程序。  
  
-   将一个 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 文件添加到项目。  
  
-   创建新的实体类。  
  
-   配置实体类使用继承。  
  
-   查询继承类。  
  
-   在 Windows 窗体上显示数据。  
  
## 创建要从中继承的表  
 为了解继承的工作方式，您将创建一个小的 Person 表用作基类，然后创建一个从该表继承的 Employee 对象。  
  
#### 创建基表以演示继承  
  
1.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，右击**“表”**节点，然后单击**“添加新表”**。  
  
    > [!NOTE]
    >  可以使用 Northwind 数据库或其他任何可添加表的数据库。  
  
2.  在表设计器中，向该表中添加以下列：  
  
    |列名|数据类型|允许为 Null|  
    |--------|----------|--------------|  
    |ID|int|False|  
    |类型|int|True|  
    |FirstName|nvarchar\(200\)|False|  
    |LastName|nvarchar\(200\)|False|  
    |经理|int|True|  
  
3.  将 ID 列设置为主键。  
  
4.  保存该表并将其命名为 Person。  
  
## 向表中添加数据  
 为了验证对继承的配置是否正确，表对于单表继承中的每个类都需要一些数据。  
  
#### 向表中添加数据。  
  
1.  在数据视图中打开该表。（在**“服务器资源管理器”**\/**“数据库资源管理器”**中右击**“Person”**表，然后单击**“显示表数据”**。）  
  
2.  将下面的数据复制到表中。（您可以在[Results Pane](http://msdn.microsoft.com/zh-cn/3c712f20-7c9f-4021-b1ac-fdc6f534c95a)中选择整行，复制数据并将数据粘贴到表中。）  
  
    ||||||  
    |-|-|-|-|-|  
    |ID|类型|FirstName|LastName|经理|  
    |1|1|Anne|Wallace|NULL|  
    |2|1|Carlos|Grilo|NULL|  
    |3|1|Yael|Peled|NULL|  
    |4|2|Gatis|Ozolins|1|  
    |5|2|Andreas|Hauser|1|  
    |6|2|Tiffany|Phuvasate|1|  
    |7|2|Alexey|Orekhov|2|  
    |8|2|Michał|Poliszkiewicz|2|  
    |9|2|Tai|Yee|2|  
    |10|2|Fabricio|Noriega|3|  
    |11|2|Mindy|Martin|3|  
    |12|2|Ken|Kwok|3|  
  
## 创建新项目  
 至此，表已经创建完毕，下面创建一个新项目演示对继承的配置。  
  
#### 创建新的 Windows 应用程序  
  
1.  从**“文件”**菜单创建一个新的项目。  
  
2.  将项目命名为 InheritanceWalkthrough。  
  
    > [!NOTE]
    >  Visual Basic 和 C\# 项目中都支持 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。请使用这两种语言之一创建新项目。  
  
3.  单击**“Windows 窗体应用程序”**模板，然后单击**“确定”**。有关更多信息，请参见 [客户端应用程序](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md)。  
  
4.  InheritanceWalkthrough 项目即被创建并添加到**“解决方案资源管理器”**中。  
  
## 将 LINQ to SQL 类文件添加到项目  
  
#### 将 LINQ to SQL 文件添加到项目  
  
1.  在**“项目”**菜单上单击**“添加新项”**。  
  
2.  单击**“LINQ to SQL 类”**模板，然后单击**“添加”**。  
  
     .dbml 文件即添加到项目，[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]打开。  
  
## 使用 O\/R 设计器创建继承  
 通过将**“继承”**对象从**“工具箱”**拖动到设计图面来配置继承。  
  
#### 创建继承  
  
1.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，定位到之前创建的**“Person”**表。  
  
2.  将**“Person”**表拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]设计图面上。  
  
3.  将另一个**“Person”**表拖动到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]并将其名称更改为“Employee”。  
  
4.  从**“Person”**对象删除**“Manager”**属性。  
  
5.  从**“Employee”**对象删除**“Type”**、**“ID”**、**“FirstName”**和**“LastName”**属性。（即删除**“Manager”**以外的所有属性。）  
  
6.  从**“工具箱”**的**“对象关系设计器”**选项卡上，在**“Person”**和**“Employee”**对象之间创建**“继承”**。为此，请单击**“工具箱”**中的**“继承”**项，然后松开鼠标按钮。接下来在 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中依次单击**“Employee”**对象和**“Person”**对象。继承连线上的箭头将指向**“Person”**对象。  
  
7.  单击设计图面上的**“继承”**连线。  
  
8.  将**“鉴别器属性”**属性设置为**“Type”**。  
  
9. 将**“派生类鉴别器值”**属性设置为**“2”**。  
  
10. 将**“基类鉴别器值”**属性设置为**“1”**。  
  
11. 将**“继承默认值”**属性设置为**“Person”**。  
  
12. 生成项目。  
  
## 查询继承类并在窗体上显示数据  
 您将向窗体中添加一些代码，用于在对象模型中查询特定的类。  
  
#### 创建一个 LINQ 查询并在窗体上显示结果  
  
1.  将一个**“ListBox”**拖动到 Form1 上。  
  
2.  双击窗体以创建 `Form1_Load` 事件处理程序。  
  
3.  将下面的代码添加到 `Form1_Load` 事件处理程序中：  
  
    ```vb#  
    Dim dc As New DataClasses1DataContext  
    Dim results = From emp In dc.Persons _  
        Where TypeOf emp Is Employee _  
        Select emp  
  
    For Each Emp As Employee In results  
        ListBox1.Items.Add(Emp.LastName)  
    Next  
    ```  
  
    ```c#  
    NorthwindDataContext dc = new DataClasses1DataContext();  
    var results = from emp in dc.Persons  
                  where emp is Employee  
                  select emp;  
  
    foreach(Employee Emp in results)  
    {  
        listBox1.Items.Add(Emp.LastName)  
    }  
    ```  
  
## 测试应用程序  
 运行应用程序并检验列表框中显示的记录是否全为员工（“Type”列值为 2 的记录）。  
  
#### 测试应用程序  
  
1.  按 F5。  
  
2.  检验是否仅显示了“Type”列值为 2 的记录。  
  
3.  关闭窗体。（在**“调试”**菜单上单击**“停止调试”**。）  
  
## 请参阅  
 [O\/R 设计器概述](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [如何：向项目中添加 LINQ to SQL 类（O\/R 设计器）](../Topic/How%20to:%20Add%20LINQ%20to%20SQL%20Classes%20to%20a%20Project%20\(O-R%20Designer\).md)   
 [演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [如何：分配存储过程以执行更新、插入和删除（O\/R 设计器）](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [如何：使用 Visual Basic 或 C\# 生成对象模型](../Topic/How%20to:%20Generate%20the%20Object%20Model%20in%20Visual%20Basic%20or%20C%23.md)