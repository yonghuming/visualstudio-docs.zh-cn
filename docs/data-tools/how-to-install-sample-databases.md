---
title: "如何：安装示例数据库 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
helpviewer_keywords: 
  - "Adventure Works 示例数据库"
  - "数据 [Visual Studio], 示例数据库"
  - "Northwind 示例数据库"
  - "示例数据库, Adventure Works"
  - "示例数据库, Northwind"
ms.assetid: ed1291f6-604c-4972-ae22-0345c6dea12e
caps.latest.revision: 56
caps.handback.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：安装示例数据库
许多数据示例都需要能够连接到 Northwind、Pubs 和 AdventureWorks 示例数据库。  你可以按照以下程序安装并连接到这些数据库。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 安装数据库  
 许多数据示例要求能够使用可从网站下载的示例数据库。  示例数据库包括 AdventureWorks、Northwind 和 Pubs 数据库。  
  
#### 安装 SQL Server 的 Northwind 和 Pubs 示例数据库  
  
1.  访问 [Northwind 和 Pubs 示例数据库](http://go.microsoft.com/fwlink?linkid=64296)网站。  
  
2.  下载并运行安装程序。  
  
     安装程序会将文件夹**“SQL Server 2000 Sample Databases”**添加到计算机的根文件夹。  （例如：**C:\\SQL Server 2000 Sample Databases**）。  
  
3.  找到你需要的数据库（Northwind 或 Pubs）的 SQL 脚本。  
  
    > [!WARNING]
    >  .MDF 数据库文件无法轻松转换为可在当前 SQL Server 版本中使用的格式，因此最好使用脚本创建数据库。  
  
4.  在**“服务器资源管理器”**中，创建与要在其中安装数据库的 SQL Server 实例间的连接。  如果没有特别要用的 SQL Server，可使用随 Visual Studio 自动安装的数据库。  为此，请指定服务器名称 `(localdb)\v11.0`。  
  
     若要创建连接，请执行以下步骤。  
  
    ###### 创建与 SQL Server 实例的连接  
  
    1.  在**“服务器资源管理器”**中，打开**“数据连接”**节点的快捷菜单，然后选择**“添加连接”**。  
  
         此时会显示**“添加连接”**对话框。  
  
    2.  输入要在其中创建 Northwind 或 Pubs 数据库的 SQL Server 的名称，或者输入 \(localdb\)\\v11.0。  
  
    3.  在**“选择或输入数据库名称”**之下，从列表中选择任意数据库，例如 tempdb。  
  
    4.  选择**“测试连接”**按钮，验证一切是否正常，然后选择**“确定”**按钮。  
  
         **“服务器资源管理器”**中将显示新连接节点。  
  
5.  在服务器连接节点的快捷菜单上，选择**“新建查询”**按钮。  
  
     编辑器窗口将打开并显示空的 .sql 脚本文件。  
  
6.  将 instnwnd.sql 或 instpubs.sql 的内容粘贴到编辑器窗口。  
  
7.  选择“执行查询”按钮（查询窗口右上方的空心绿色三角图标）。  
  
     如果成功执行查询，则会显示“命令已成功完成”消息。  这意味着 Northwind 或 pubs 数据库创建完成。  
  
     你仍要添加连接到示例数据库。  在“服务器资源管理器”中，打开“数据连接”节点的快捷菜单，然后选择“添加连接”。  
  
8.  选择之前已选的数据库服务器，但是在“选择或输入数据库名称”之下选择 Northwind 或 pubs 数据库，然后选择“确定”按钮。  
  
     “数据库连接”之下显示示例数据库新节点。  
  
9. 关闭编辑器窗口，确认不保存查询文件。  成功创建数据库之后便不必保存数据库创建脚本。  
  
#### 安装 AdventureWorks 示例数据库  
  
-   访问 [CodePlex 网站](http://go.microsoft.com/fwlink/?linkid=87843)下载 AdventureWorks 示例数据库。  
  
#### 安装 Microsoft Access 的 Northwind 示例数据库  
  
1.  对于 Microsoft Access 2010 和更高版本，搜索 Northwind 的联机模板，然后选择“桌面 Northwind 2007 示例数据库”。  
  
2.  在 Mocrosoft Access 中，将数据库文件保存为 Northwind.accdb。  
  
 Access 数据库的新扩展名是 .accdb。  请参阅[使用 Microsoft Access 2010 进行数据编程](http://msdn.microsoft.com/library/office/ff965871.aspx)。  要使用 Access 连接到 Northwind 数据库，请参阅[如何：连接到 Northwind 数据库](../data-tools/how-to-connect-to-the-northwind-database.md)。  
  
## .NET Framework 安全性  
 示例数据库仅用于演示目的，未必展示了最佳安全实践。  
  
## 请参阅  
 [如何确定 SQL Server 及其组件的版本](http://support.microsoft.com/kb/321185)   
 [演练：在 Visual Studio 中创建本地数据库文件](../data-tools/create-a-sql-database-by-using-a-designer.md)   
 [如何：连接到 Northwind 数据库](../data-tools/how-to-connect-to-the-northwind-database.md)