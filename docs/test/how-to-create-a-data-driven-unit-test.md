---
title: "如何：创建数据驱动的单元测试 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "单元测试, 运行"
  - "单元测试, 数据驱动"
  - "数据驱动的单元测试"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 33
---
# 如何：创建数据驱动的单元测试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用托管代码的 Microsoft 单元测试框架，您可以从数据源中设置单元测试方法以检索测试方法中使用的值。  该方法依次对各行中的数据源中运行，通过使用单一方法，可以轻松测试各种输入。  
  
 本主题包含以下各节：  
  
-   [被测试的方法。](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [创建数据源](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [添加一个TestContext 到测试类](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [编写测试方法。](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [指定 DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [使用TestContext.DataRow 访问数据](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [运行测试并查看结果](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 创建数据驱动单元测试包含以下步骤：  
  
1.  创建一个包含测试方法中使用的值的数据源。  数据源可以是计算机上注册执行的任何测试类型。  
  
2.  添加一个私有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 字段和一个公有的 `TestContext` 属性到测试类。  
  
3.  创建一个单元测试方法并添加一个 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 特性到它。  
  
4.  使用<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> 索引器属性检索测试中使用的值。  
  
##  <a name="BKMK_The_method_under_test"></a> 被测试的方法。  
 例如，假定我们已经创建了：  
  
1.  接受并处理不同类型的帐户的交易的解决方案调用 `MyBank`。  
  
2.  `MyBank` 的项目调用 `BankDb`来管理帐户的事务。  
  
3.  类调用`DbBank` 项目的 `Maths`确保执行数学函数的所有事务是对银行是有利的。  
  
4.  单元测试项目调用 `BankDbTests` 来测试`BankDb`组件的行为。  
  
5.  单元测试类调用 `MathsTests` 验证`Maths` 类的行为。  
  
 我们将测试`Maths` 的方法，它使用循环来添加两个整数：  
  
```  
public int AddIntegers(int first, int second)  
{  
    int sum = first;  
    for( int i = 0; i < second; i++)  
    {  
        sum += 1;  
    }  
    return sum;  
}  
```  
  
##  <a name="BKMK_Creating_a_data_source"></a> 创建数据源  
 若要测试 `AddIntegers` 方法，我们创建一个参数为用于指定范围值总和和希望返回的数据源。  在我们的示例中，我们创建 SQL 数据库协定名称 `MathsData` 和包含的列名和值名为 `AddIntegersData` 的表  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> 添加一个TestContext 到测试类  
 单元测试框架创建 一个`TestContext` 对象来存储一个数据驱动测试数据源的信息。  该框架然后设置此对象作为我们创建 `TestContext`的属性的值。  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 在测试方法中，可以通过 `TestContext`的 `DataRow` 索引器属性访问数据。  
  
##  <a name="BKMK_Writing_the_test_method"></a> 编写测试方法。  
 对 `AddIntegers` 的测试方法相当简单。  对于数据源中的每行，调用 `AddIntegers` 及 **FirstNumber** 和作为参数的 **SecondNumber** 列值，因此，我们验证返回值 **Sum** 列值：  
  
```  
  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]  
[TestMethod()]  
public void AddIntegers_FromDataSourceTest()  
{  
    var target = new Maths();  
  
    // Access the data  
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);   
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);  
    int actual = target.IntegerMethod(x, y);  
    Assert.AreEqual(expected, actual,  
        "x:<{0}> y:<{1}>",  
        new object[] {x, y});  
  
}  
  
```  
  
 注意 `Assert` 方法包含显示了不合格迭代的 `x` 和 `y` 值的消息。  默认方式，断言的值，`expected` 和 `actual`，已包含在不合格的测试的详细信息中。  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> 指定 DataSourceAttribute  
 `DataSource` 特性为数据源以及在测试方法使用表的名称指定连接字符串。  根据使用的数据源的种类，连接字符串中的确切信息会有所不同。  在此示例中，使用 SqlServerCe 数据库。  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 DataSource 特性具有三个构造函数。  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 具有一个参数的构造函数在使用解决方案的 app.config 文件中存储的连接信息。  *dataSourceSettingsName* 为 指定连接信息的设置文件中的XML 元素的名称。  
  
 使用 app.config 文件允许您是无需更改单元测试自身，即可更改数据源的位置。  有关如何创建和使用 app.config 文件的信息，请参见[演练：使用配置文件定义数据源](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)。  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 带有两个参数的 `DataSource` 构造函数指定数据源和数据包含为测试方法的表名连接字符串。  
  
 连接字符串取决于数据源的类型，但是，它包含应指定提供程序数据的固定名称的提供程序元素。  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> 使用TestContext.DataRow 访问数据  
 若要访问 `AddIntegersData` 的数据表，请使用 `TestContext.DataRow` 索引器。  `DataRow` 是 <xref:System.Data.DataRow> 对象，因此，我们通过列索引或名称检索列值。  由于返回值作为对象，我们需要将其强制转换为适当的类型：  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> 运行测试并查看结果  
 编写完测试方法时，请生成测试项目。  测试方法保存在 未运行的测试  组中显示测试资源管理器窗口。  当您运行、编写和重新运行测试时，测试资源管理器将在“未通过的测试”、“已通过的测试”、“跳过的测试”组中显示结果。  你可以选择运行所有来运行所有测试，或选择运行来运行测试子集。  
  
 测试结果条在资源管理器顶部动画作为测试运行。  测试运行结束时，如果测试方法全部通过，状态栏将变为绿色；如果有任何测试失败，状态栏将变为红色。  测试运行的摘要显示在资源管理器窗口的底部的详细信息窗格。  选择一个测试,在底部窗格中查看该测试的详细信息。  
  
 如果运行了此示例中的 `AddIntegers_FromDataSourceTest` 方法，结果栏将变为红色，而测试方法移动到 失败的测试，如果任意从数据源中循环访问方法失败则数据驱动测试失败。  在选择测试资源管理器窗口中的不合格的数据驱动测试，细节窗格中显示由数据列索引标识的每个迭代的结果。  在此示例中，显示了 `AddIntegers` 算法无法正确处理负值。  
  
 当所测试的方法时正确的且该测试重新运行时，结果条变成绿色，而测试方法移动到通过的测试  组。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [如何：创建和运行单元测试](http://msdn.microsoft.com/zh-cn/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [单元测试代码](../test/unit-test-your-code.md)   
 [使用测试资源管理器运行单元测试](../test/run-unit-tests-with-test-explorer.md)   
 [用 Microsoft 适用于托管代码的单元测试框架编写 .NET Framework 的单元测试](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)