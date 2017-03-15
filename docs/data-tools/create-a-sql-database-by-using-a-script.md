---
title: "演练：创建小示例数据库 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：创建小示例数据库
在本演练中，使用 Visual Studio 创建一个小型数据库，该数据库包含[演练：使用 ADO.NET 创建简单的数据应用程序](../data-tools/create-a-simple-data-application-by-using-adonet.md)的示例代码。  
  
 **主题内容**  
  
-   [创建包含数据库架构的脚本](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [创建数据库项目并导入架构](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [部署数据库](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## 系统必备  
 为了完成本演练，计算机上必须装有 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]。  还必须能够连接到您在其上有权创建和部署数据库的数据库服务器或 LocalDB 数据库。  
  
##  <a name="CreateScript"></a> 创建包含数据库架构的脚本  
  
#### 创建可从中导入架构的脚本  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的菜单栏上，选择**“文件”**、**“新建”**、**“文件”**。  
  
     此时出现**“新建文件”**对话框。  
  
2.  在“类别”列表中，选择“常规”。  
  
3.  在“模板”列表中，选择“Sql 文件”，然后选择“打开”按钮。  
  
     将打开 Transact\-SQL 编辑器。  
  
4.  复制下面的 Transact\-SQL 代码并将其粘贴到 Transact\-SQL 编辑器中。  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  在菜单栏上，依次选择“文件”、“将 SqlQuery\_1.sql 另存为”。  
  
     将出现**“另存文件为”**对话框。  
  
6.  在“文件名”框中，输入 `SampleImportScript.sql`，请注意文件的保存位置，然后选择“保存”按钮。  
  
7.  在菜单栏上，依次选择“文件”、“关闭解决方案”。  
  
     接下来，创建一个数据库项目，并从已创建的脚本导入架构。  
  
##  <a name="CreateProject"></a> 创建数据库项目并导入架构  
  
#### 创建数据库项目  
  
1.  在菜单栏上，选择**“文件”**，**“新建**、**“项目”**。  
  
     此时将出现“新建项目”对话框。  
  
2.  在“已安装”下，展开“模板”节点，展开“其他语言”节点，选择“SQL Server”类别，然后选择“SQL Server 数据库项目”模板。  
  
    > [!NOTE]
    >  “其他语言”节点不在 Visual Studio 的所有安装中显示。  
  
3.  在“名称”框中，输入`“Small Database”`。  
  
4.  如果“创建解决方案的目录”复选框尚未选中，则选择该复选框。  
  
5.  如果“添加到源代码管理”复选框尚未清除，则清除该复选框，并选择“确定”按钮。  
  
     数据库项目会创建并出现在**“解决方案资源管理器”**中。  
  
     接下来，从脚本中导入数据库架构。  
  
#### 从脚本中导入数据库  
  
1.  在菜单栏上，依次选择“项目”、“导入”、“脚本”。  
  
2.  在“欢迎”页上，查看文本，然后选择“下一个”按钮。  
  
3.  选择“单个文件”选项按钮，然后选择“浏览”按钮。  
  
     将出现“导入SQL 脚本”对话框。  
  
4.  打开保存 SampleImportScript.sql 文件的文件夹，选择该文件，然后选择“打开”按钮。  
  
5.  选择“完成”按钮关闭“导入 SQL 脚本”对话框。  
  
     将导入脚本，在该脚本中定义的对象添加到数据库项目中。  
  
6.  查看摘要，然后选择“完成”按钮关闭“导入 SQL 脚本文件”对话框。  
  
7.  在“解决方案资源管理器”中，展开项目的“销售”、“脚本”和“安全性”文件夹，并验证其是否包含 .sql 文件。  
  
8.  在“SQL Server 对象资源管理器”中，验证数据库显示在“项目”节点下。  
  
     此时，数据库只包含系统对象，如表和存储过程。  在部署数据库后，它将包含脚本定义的用户表和存储过程。  
  
##  <a name="DeployDatabase"></a> 部署数据库  
 当您按 F5 键时，将默认向 LocalDB 数据库部署（或发布）该数据库。  可以通过打开项目的属性页，选择“调试”选项卡，然后更改连接字符串将数据库部署到其他位置。