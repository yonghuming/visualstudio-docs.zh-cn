---
title: "如何：连接到 Northwind 数据库 | Microsoft Docs"
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
helpviewer_keywords: 
  - "连接 [Visual Studio], Northwind 数据库"
  - "Northwind 示例数据库"
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 如何：连接到 Northwind 数据库
当你了解如何使用 Visual Studio 创建数据库应用程序时，你将需要连接到 Northwind 数据库，以按照该产品文档中的多个示例进行操作。  根据你要遵循的示例，你将连接到  SQL Server 或数据库文件中的数据库，例如，适用于 Microsoft Access 或 SQL Server 的一个数据库。  
  
## 创建到 Northwind 数据库的数据连接  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 创建到 Northwind 数据库（SQL Server）的数据连接  
  
1.  在**“视图”**菜单上，选择**“服务器资源管理器”**\/**“数据库资源管理器”**。  
  
2.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，打开**“数据连接”**的快捷菜单，然后选择**“添加连接”**。  
  
     选择**“添加连接”**后，将显示**“选择数据源”**对话框或**“添加连接”**对话框。  
  
3.  如果显示**“选择数据源”**对话框，请选择**“Microsoft SQL Server”**，然后选择**“确定”**。  
  
     如果显示**“添加连接”**对话框，但**“数据源”**不是**“Microsoft SQL Server \(SqlClient\)”**，请选择**“更改”**按钮以打开**“更改数据源”**对话框、选择**“Microsoft SQL Server”**，然后选择**“确定”**按钮。  
  
4.  在**“服务器名称”**列表中，指定 Northwind 数据库所在的服务器的名称。  
  
5.  根据 SQL Server 或 Northwind 数据库的版本的要求，选择**“使用 Windows 身份验证”**或**“使用 SQL Server 身份验证”**，并输入用户名和密码以登录到运行 SQL Server 的计算机。  
  
6.  在**“选择或输入数据库名称”**列表中选择 Northwind 数据库。  
  
7.  选择**“测试连接”**以验证到 Northwind 数据库的连接。  
  
8.  选择**“确定”**。  
  
     到 Northwind 数据库的数据连接将会添加到**“服务器资源管理器”**\/**“数据库资源管理器”**中。  
  
 除了连接到 SQL Server 数据库的远程实例外，你还可以直接连接到包含该数据库的实际文件。  这样，你就可以将数据库文件直接添加到项目中，在该项目中可将这些文件部署为应用程序的一部分。  当前支持的本地数据库文件包括：SQL Server Compact 数据库文件 \(.sdf\)、[!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 和 SQL Server Express 数据库文件 \(.mdf\)，以及 Microsoft Access 数据库文件（.mdb 或 .accdb）。  
  
#### 创建到 Northwind 数据库的数据连接 – SQL Server 数据库文件 \(.mdf\)  
  
1.  在**“视图”**菜单上，选择**“服务器资源管理器”**\/**“数据库资源管理器”**。  
  
2.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，打开**“数据连接”**的快捷菜单，然后选择**“添加连接”**。  
  
     选择**“添加连接”**后，将显示**“添加连接”**对话框或**“选择数据源”**对话框。  
  
3.  如果显示**“选择数据源”**对话框，请选择**“Microsoft SQL Server 数据库文件”**，然后选择**“确定”**。  
  
4.  如果显示**“添加连接”**对话框，请验证是否已将**“数据源”**设置为**“Microsoft SQL Server 数据库文件 \(SqlClient\)”**。  如果未设置为**“Microsoft SQL Server 数据库文件 \(SqlClient\)”**，请选择**“更改”**以打开**“更改数据源”**对话框、选择**“Microsoft SQL Server 数据库文件”**，然后选择**“确定”**按钮。  
  
5.  选择**“浏览”**以查找包含 Northwind 数据库的 .mdf 文件。  
  
6.  根据 Northwind 数据库的版本的要求，选择**“使用 Windows 身份验证”**或**“SQL Server 身份验证”**，并输入用户名和密码以登录到运行 SQL Server 的计算机。  
  
7.  选择**“确定”**按钮。  
  
     到 Northwind 数据库的数据连接将会添加到**“服务器资源管理器”**\/**“数据库资源管理器”**中。  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 具有应用到 Northwind 数据库文件 \(.mdf\) 的更改。  相关信息，请参阅[如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)。  
  
#### 创建与 Northwind 数据库的数据连接 — Access 数据库文件 \(.mdb 或 .accdb\)  
  
1.  在**“视图”**菜单上，选择**“服务器资源管理器”**\/**“数据库资源管理器”**。  
  
2.  在**“服务器资源管理器”**\/**“数据库资源管理器”**中，打开**“数据连接”**的快捷菜单，然后选择**“添加连接”**。  
  
     选择**“添加连接”**后，将显示**“添加连接”**对话框或**“选择数据源”**对话框。  
  
3.  如果显示**“选择数据源”**对话框，请选择**“Microsoft Access 数据库文件”**，然后选择**“确定”**。  
  
4.  如果显示**“添加连接”**对话框，请验证是否将**“数据源”**设置为**“Microsoft Access 数据库文件”**。  如果未设置为**“Microsoft Access 数据库文件”**，请选择**“更改”**以打开**“更改数据源”**对话框、选择**“Microsoft Access 数据库文件”**，然后选择**“确定”**按钮。  
  
5.  选择**“浏览”**以查找包含 Northwind 数据库的 .mdb 或 .accdb 文件。  
  
6.  如果你的 Northwind 数据库版本要求用户名和密码，请输入用户名和密码。  
  
7.  选择**“确定”**。  
  
     到 Northwind 数据库的数据连接将会添加到**“服务器资源管理器”**\/**“数据库资源管理器”**中。  
  
## 请参阅  
 [如何：安装示例数据库](../data-tools/how-to-install-sample-databases.md)   
 [使用 Microsoft Access 2010 进行数据编程](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [数据演练](../Topic/Data%20Walkthroughs.md)