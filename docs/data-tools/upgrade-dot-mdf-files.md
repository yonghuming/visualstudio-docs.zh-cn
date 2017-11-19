---
title: "升级.mdf 文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 8ed511eed7b0ace46bbc61c1d486ade608d4b5a5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="upgrade-mdf-files"></a>升级.mdf 文件
本主题介绍用于在安装了较新版本的 Visual Studio 后再升级您的数据库文件 (.mdf) 的选项。 它包括以下任务的说明：  
  
-   升级数据库文件，以使用较新版本的 SQL Server Express LocalDB  
  
-   升级数据库文件，以使用较新版本的 SQL Server Express  
  
-   与 Visual Studio 中的数据库文件的工作，但保留了与 SQL Server Express 或 LocalDB 的较旧版本的兼容性  
  
-   使 SQL Server Express 的默认数据库引擎  
  
你可以使用 Visual Studio 打开包含已通过使用 SQL Server Express 或 LocalDB 的较旧版本的数据库文件 (.mdf) 的项目。 但是，若要继续开发 Visual Studio 中的项目，你必须具有该版本的 SQL Server Express 或 LocalDB 安装在与 Visual Studio 中，相同的计算机上，或者你必须先升级数据库文件。 如果升级数据库文件，你将无法访问它通过使用较旧版本的 SQL Server Express 或 LocalDB。  
  
你可能还会提示您升级通过 SQL Server Express 或 LocalDB 的早期版本创建，如果文件的版本与 SQL Server Express 或 LocalDB 当前已安装的实例的不兼容的数据库文件。 若要解决此问题，Visual Studio 将提示你升级该文件。  
  
> [!IMPORTANT]
> 我们建议在升级之前备份数据库文件。  
  
> [!WARNING]
> 如果升级到 LocalDB 2016 (V13) 的 32 位在 LocalDB 2014 (V12) 中创建的.mdf 文件或更高版本，你将无法在 LocalDB 的 32 位版本中再次打开该文件。
  
将数据库升级之前，请考虑以下条件：  
  
-   不升级，如果你想要在较旧版本和较新版本的 Visual Studio 中的项目上工作。  
  
-   不升级，如果你的应用程序将在使用 SQL Server Express 而不是 LocalDB 的环境中使用。  
  
-   不升级如果你的应用程序使用远程连接，因为 LocalDB 不接受这些条款。  
  
-   如果你的应用程序依赖于 Internet 信息服务 (IIS) 的情况下不进行升级。  
  
-   如果你想要在一个沙盒环境中测试数据库应用程序，但不想管理数据库，请考虑升级。  
  
### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>若要升级的数据库文件使用的 LocalDB 版本
  
1.  在**服务器资源管理器**，选择**连接到数据库**按钮。  
  
2.  在**添加连接**对话框框中，指定以下信息：  
  
    -   **数据源**:`Microsoft SQL Server (SqlClient)`  
  
    -   **服务器名称**:  
  
        -   若要使用的默认版本： `(localdb)\MSSQLLocalDB`。  这将指定 ProjectV12 或 ProjectV13，具体取决于所安装的 Visual Studio 的版本和创建的第一个的 LocalDB 实例时。 **MSSQLLocalDB**中的节点**SQL Server 对象资源管理器**哪个版本指向所示。  
  
        -   若要使用的特定版本：`(localdb)\ProjectsV12`或`(localdb)\ProjectsV13`，其中 V12 是 LocalDB 2014，V13 是 LocalDB 2016。  
  
    -   **将数据库文件附加**： 主.mdf 文件的物理路径。  
  
    -   **逻辑名称**： 你想要使用与文件的名称。  
  
3.  选择“确定”按钮。  
  
4.  当系统提示你时，选择**是**按钮以升级该文件。  
  
    数据库将升级、 附加到 LocalDB 数据库引擎，并且不再与 LocalDB 的较旧版本兼容。  
  
你还可以修改要通过打开连接的快捷菜单，然后选择使用 LocalDB 的 SQL Server Express 连接**修改连接**。 在**修改连接**对话框框中，服务器名称更改为`(LocalDB)\MSSQLLocalDB`。 在**高级属性**对话框框中，请确保**用户实例**设置为**False**。

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>若要升级的数据库文件要使用的 SQL Server Express 版本  
  
1.  在连接到数据库的快捷菜单，选择**修改连接**。  
  
2.  在**修改连接**对话框中，选择**高级**按钮。  
  
3.  在**高级属性**对话框中，选择**确定**而无需更改服务器名称的按钮。  
  
    数据库文件升级到匹配当前版本的 SQL Server Express。  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>若要使用 Visual Studio 中的数据库，但保留与 SQL Server Express 的兼容性  
  
-   在 Visual Studio 中，无需立即升级打开的项目。  
  
    -   若要运行该项目，选择**F5**密钥。  
  
    -   若要编辑数据库，请打开中的.mdf 文件**解决方案资源管理器**，并展开中的节点**服务器资源管理器**要使用你的数据库。  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>若要使 SQL Server Express 默认数据库引擎  
  
1.  在菜单栏上，选择**工具**，**选项**。  
  
2.  在**选项**对话框框中，展开**数据库工具**选项，，然后选择**数据连接**。  
  
3.  在**SQL Server 实例名称**文本框中，指定的 SQL Server Express 或你想要使用的 LocalDB 实例的名称。 如果未命名的实例，指定`.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`。  
  
4.  选择“确定”按钮。  
  
    SQL Server Express 将你的应用程序的默认数据库引擎。

## <a name="see-also"></a>请参阅
[在 Visual Studio 中访问数据](accessing-data-in-visual-studio.md)
