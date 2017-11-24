---
title: "Visual Studio 数据库兼容性 |Microsoft 文档"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 17bdaffa8fdbb6ddff9d7fe5590db021997aa01f
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio 的兼容的数据库系统

若要开发 Visual Studio 中的数据连接应用程序，你通常在您的本地开发计算机上安装数据库系统，然后部署应用程序和数据库到生产环境准备好时。 Visual Studio 的一部分您的计算机上安装 SQL Server Express LocalDB**数据存储和处理**工作负荷。 此 LocalDB 实例可用于快速、 轻松地开发数据连接的应用程序。

对于数据库系统，可从.NET 应用程序，并在 Visual Studio 数据工具窗口中均可见，它必须具有的 ADO.NET 数据提供程序。 如果你打算在.NET 应用程序中使用实体数据模型，一个提供程序必须专门支持实体框架。 通过 NuGet 包管理器或通过 Visual Studio 应用商店提供许多提供程序。

如果你使用 Azure 存储 Api，安装 Azure 存储仿真程序在本地计算机上在开发过程才能避免产生费用，直到你准备好部署到生产环境。 有关详细信息，请参阅[使用 Azure 存储模拟器进行开发和测试](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/)。

以下列表包含的一些更受欢迎的数据库系统，可以使用 Visual Studio 项目中。 列表并不详尽。 提供 ADO.NET 数据提供程序，Visual Studio 工具与深度集成的第三方供应商列表，请参阅[ADO.NET 数据提供程序](https://msdn.microsoft.com/en-us/library/dd363565.aspx)。

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server 是 Microsoft 旗舰数据库产品。 SQL Server 2016 提供了性能有所突破、 高级的安全和丰富、 集成的报告和分析。 中用于不同的用途设计的各种版本附带了它： 从高度可扩展、 高性能的业务分析，一台计算机上使用。 SQL Server Express 是适用于重新分发和嵌入的 SQL Server 的全功能版本。  LocalDB 是 SQL Server Express 不需要配置并运行应用程序的进程的简化的版本。 你可以下载中的一个或两个产品[SQL Server Express 下载页面](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)。 许多本部分中的 SQL 示例使用 SQL Server LocalDB。 SQL Server Management Studio (SSMS) 是一个独立的数据库管理应用程序具有更多的功能比 Visual Studio SQL Server 对象资源管理器中提供的内容。 你可以从的上一页链接获取 SSMS。

## <a name="oracle"></a>Oracle

你可以下载的付费版本或免费版本中的 Oracle 数据库[Oracle 技术网络](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)页。 对于实体框架和 Tableadapter 的设计时支持，你将需要[Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)。 其他正式的 Oracle 产品，包括 Oracle 即时客户端，可通过 NuGet 包管理器。  你可以通过中的说明下载 Oracle 示例架构[Oracle 联机文档](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)。

## <a name="mysql"></a>MySQL

MySQL 是一个受欢迎的开源数据库系统，在企业和网站中广泛使用。 有关 MySQL 的下载，Visual Studio 中，以及相关的产品 MySQL 位于[Windows 上的 MySQL](http://www.mysql.com/why-mysql/windows/)。  第三方提供各种 Visual Studio 扩展和 mysql 的独立管理应用程序。 你可以浏览产品在 NuGet 包管理器 (**工具** > **NuGet 包管理器** > **管理解决方案的 NuGet 包**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL 是一个免费的开源对象关系数据库系统。 若要在 Windows 上安装它，你可以从下载[PostgreSQL 下载页](http://www.postgresql.org/download/windows/)。  你也可以从源代码生成 PostgreSQL。  PostgreSQL 核心系统包括 C 语言界面。 许多第三方提供了有关从.NET 应用程序中使用 PostgreSQL 的 NuGet 包。  你可以浏览产品在 NuGet 包管理器 (**工具** > **NuGet 包管理器** > **管理解决方案的 NuGet 包**). 可能是最常用的包提供的[npgsql.org](http://www.npgsql.org)。

## <a name="sqlite"></a>SQLite

SQLite 是嵌入的 SQL 数据库引擎在应用程序自身的进程中运行。 你可以下载它从[SQLite 下载页](http://www.sqlite.org/download.html)。 SQLite 的许多第三方 NuGet 包，还提供。 你可以浏览产品在 NuGet 包管理器 (**工具** > **NuGet 包管理器** > **管理解决方案的 NuGet 包**).

## <a name="firebird"></a>Firebird

Firebird 是一种开放源代码 SQL 数据库系统。 你可以下载它从[Firebird 下载页](http://firebirdsql.org/en/downloads/)。 ADO.NET 数据提供程序是通过 NuGet 包管理器中可用。

## <a name="see-also"></a>请参阅

[在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)  
[如何确定的版本和 SQL Server 及其组件的版本](http://support.microsoft.com/kb/321185)