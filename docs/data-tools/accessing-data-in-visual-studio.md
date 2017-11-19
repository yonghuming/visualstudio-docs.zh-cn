---
title: "访问 Visual Studio 中的数据 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 585f021bf88dd6005a82643c5d182bd1fcbf8e91
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="accessing-data-in-visual-studio"></a>访问 Visual Studio 中的数据
在 Visual Studio 中，你可以创建连接到几乎任何数据库产品或服务，采用何种格式，任何位置中的数据的应用程序 — 在本地计算机上，在本地网络，或在公共、 私有、 或混合云。  
  
对于 JavaScript、 Python、 PHP、 Ruby 或 c + + 中的应用程序，你连接到数据就像任何其他，通过获取库并编写代码。 对于.NET 应用程序，Visual Studio 提供可用于浏览数据源，创建对象模型存储和操作数据在内存中，并将数据绑定到用户界面的工具。 Microsoft Azure 提供适用于连接到 Azure 存储的.NET、 Java、 Node.js、 PHP、 Python、 Ruby，和移动应用和 Visual Studio 中的工具 Sdk。  
  
以下列表显示从 Visual Studio 只是几个可以使用许多数据库和存储系统。 [Microsoft Azure](https://azure.microsoft.com/)产品是数据服务，包括所有设置和管理基础数据存储区。  [Azure Tools for Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx)是使您能够直接从 Visual Studio 的 Azure 数据存储区的可选组件。 可以在本地计算机上，在本地网络上，或在 Microsoft Azure 的虚拟机上托管的其他 SQL 和 NoSQL 数据库产品此处列出的大多数。 在此方案中，你负责管理数据库本身。  
  
**Microsoft Azure**  
  
||||  
|-|-|-|  
|SQL 数据库|DocumentDB|存储 （blob、 表、 队列、 文件）|  
|SQL 数据仓库|SQL Server Stretch Database|StorSimple|  
  
和的详细信息...  
  
**SQL**  
  
||||  
|-|-|-|  
|SQL Server 2005-2016，包括 Express 和 LocalDB|Firebird|MariaDB|  
|MySQL|Oracle|PostgreSQL|  
|SQLite|||  
  
和的详细信息...  
  
**NoSQL**  
  
||||  
|-|-|-|  
|Apache Cassandra|CouchDB|MongoDB|  
|NDatabase|OrientDB|RavenDB|  
|VelocityDB|||  
  
和的详细信息...  
  
许多数据库供应商和第三方通过 NuGet 包来支持 Visual Studio 集成。 在 nuget.org 上或通过 NuGet 包管理器在 Visual Studio 中，你可以浏览产品 (**工具** > **NuGet 包管理器** > **管理 NuGet解决方案包**)。 其他数据库产品与 Visual Studio 集成扩展。 你可以通过导航到浏览这些产品/服务在 Visual Studio 库**工具** > **扩展和更新**，然后选择**联机**左侧对话框中的窗格。 有关详细信息，请参阅[安装数据库系统、 工具和示例](../data-tools/installing-database-systems-tools-and-samples.md)。  
  
> [!NOTE]
> 对 SQL Server 2005 的延长的支持已于 2016 年 4 月 12 日结束。 没有数据工具在 Visual Studio 2015 及更高版本将继续使用 SQL Server 2005 在此日期之后能保证。 有关详细信息，请参阅[为 SQL Server 2005 结束支持公告](https://www.microsoft.com/server-cloud/products/sql-server-2005/)。  
  
### <a name="net-languages"></a>.NET 语言  
所有.NET 数据访问，包括在.NET 核心中都基于 ADO.NET 中，为访问任何类型的数据源、 关系和非关系定义一个接口的一组类。 Visual Studio 具有几个工具和设计器，可使用 ADO.NET 来帮助你连接到数据库，操作数据，并向用户显示数据。 此部分中的文档介绍如何使用这些工具。 你可以直接对 ADO.NET 命令对象进行编程。 有关直接调用 ADO.NET Api 的详细信息，请参阅[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) MSDN 库中。  
  
专门与 ASP.NET 相关的数据访问文档，请参阅[使用数据](http://www.asp.net/web-forms/overview/presenting-and-managing-data)ASP.NET 站点上。 有关使用使用 ASP.NET MVC 的 Entity Framework 的教程，请参阅[Getting Started with Entity Framework 6 Code First 使用 MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)。  
  
在 C# 或 Visual Basic 中的通用 Windows 平台 (UWP) 应用程序可以使用 Microsoft Azure SDK for.NET 来访问 Azure 存储空间和其他 Azure 服务。 Windows.Web.HttpClient 类，可与任何 RESTful 服务的通信。 有关详细信息，请参阅[如何连接到 HTTP 服务器是使用 Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)。  
  
对于本地计算机上的数据存储，建议的方法是使用 SQLite，在与应用程序相同的进程中运行。 如果需要对象关系映射 (ORM) 层，你可以使用实体框架。 有关详细信息，请参阅[数据访问](https://msdn.microsoft.com/windows/uwp/data-access/index)Windows 开发人员中心中。  
  
如果你要连接到 Azure 服务，请务必下载最新[Azure SDK 工具](https://azure.microsoft.com/downloads/)。  
  
#### <a name="data-providers"></a>数据提供程序  
要使数据库可以在 ADO.NET 中使用，它必须有一个自定义*ADO.NET 数据提供程序*或其他必须公开一个 ODBC 或 OLE DB 接口。 Microsoft 提供了[ADO.NET 数据提供程序的列表](https://msdn.microsoft.com/data/dd363565)SQL Server 产品以及 ODBC 和 OLE DB 提供程序。  
  
#### <a name="data-modeling"></a>数据建模  
在.NET 中，你有用于建模和操作在内存中的数据后已从数据源中检索的三个选择：  
  
[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
首选的 Microsoft ORM 技术。 你可以使用它到对关系数据的程序作为第一类的.NET 对象。 对于新应用程序，它应为默认的第一个选项，需要一个模型时。 它需要自定义支持的基础的 ADO.NET 提供程序。  
  
[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
更早版本生成对象关系映射器。 它非常适用于不太复杂的方案，但不再正处于积极开发。  
  
[数据集](../data-tools/dataset-tools-in-visual-studio.md)  
最早的三种建模技术。 它主要用于快速开发"forms over data"应用程序在其中你未处理大量数据或执行复杂的查询或转换。 数据集对象包含的数据表和 DataRow 逻辑上而不是.NET 对象更类似于 SQL 数据库对象的对象。 对于基于 SQL 数据源相对简单的应用程序，数据集可能仍是一个不错的选择。  
  
没有无需使用任何一种技术。 在某些情况下，尤其是在性能非常重要，你可以只需使用 DataReader 对象从数据库读取，并将你所需的值复制到一个集合对象，如列表\<T >。  
  
### <a name="native-c"></a>本机 C++  
连接到 SQL Server 的 c + + 应用程序应使用[Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)在大多数情况下。 如果链接服务器，则是必需的 OLE DB 和为此你使用[SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)。 你可以通过使用访问其他数据库[ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx)或 OLE DB 驱动程序直接。 ODBC 是当前的标准数据库接口，但大多数数据库系统提供无法通过 ODBC 接口访问的自定义功能。 OLE DB 是一项传统 COM 数据访问技术仍受支持但不建议用于新应用程序。 有关详细信息，请参阅[Visual c + + 中的数据访问](https://docs.microsoft.com/cpp/data/)。  
  
使用 REST 服务的 c + + 程序可以使用[c + + REST SDK](https://github.com/Microsoft/cpprestsdk)。  
  
使用 Microsoft Azure 存储空间的 c + + 程序可以使用[Microsoft Azure 存储客户端](http://www.nuget.org/packages/wastorage)。
  
数据建模&mdash;Visual Studio 不提供针对 c + + 的 ORM 层。 [ODB](http://www.codesynthesis.com/products/odb/)流行的开放源代码 ORM 为 c + +。  

若要了解有关从 c + + 应用连接到数据库的详细信息，请参阅[用于 c + + 的 Visual Studio data tools](../data-tools/visual-studio-data-tools-for-cpp.md)。 有关以前的 Visual c + + 数据访问技术的详细信息，请参阅[数据访问](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b)。
  
### <a name="javascript"></a>JavaScript  
[Visual Studio 中的 JavaScript](https://msdn.microsoft.com/library/hh334522.aspx)是用于构建跨平台应用、 UWP 应用、 云服务、 网站和 web 应用的一级语言。 可以使用 Bower、 Grunt、 Gulp、 npm 和从 Visual Studio 中的 NuGet 安装你最喜欢的 JavaScript 库和的数据库产品。 连接到 Azure 存储空间和服务通过下载 Sdk 从[Azure 网站](https://azure.microsoft.com/)。 Edge.js 是连接到 ADO.NET 数据源的服务器端 JavaScript (Node.js) 的库。  
  
### <a name="python"></a>Python  
安装[Python Tools for Visual Studio](http://microsoft.github.io/PTVS/)以及你最喜欢的 Python framework 框架来创建 CPython 或 IronPython (.NET) 应用程序。 Python Tools for Visual Studio 网站已连接到数据，包括几个教程[Django 和 SQL 数据库在 Azure 上](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure)， [Django 和在 Azure 上的 MySQL](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure)和[Bottle 和 MongoDB 上Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure)。
  
## <a name="related-topics"></a>相关主题  
 [数据、 设备和分析](https://msdn.microsoft.com/data-and-devices)  
 提供给 Microsoft 智能云，包括 Cortana Analytics Suite 和物联网的支持的介绍。  
  
 [Microsoft Azure 存储空间](https://azure.microCsoft.com/documentation/services/storage/)  
 介绍 Azure 存储空间，以及如何使用 Azure blob、 表、 队列和文件创建应用程序。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/documentation/services/sql-database/)  
 介绍如何连接到 Azure SQL 数据库，关系数据库即服务。  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 描述简化设计，浏览、 测试和部署的数据连接的应用程序和数据库的工具。  
  
 [ADO.NET](/dotnet/framework/data/adonet/index)  
 描述 ADO.NET 结构以及如何使用 ADO.NET 类来管理应用程序数据并与数据源和 XML 进行交互。  
  
 [ADO.NET 实体框架](https://msdn.microsoft.com/data/ef)  
 描述如何创建允许开发人员对概念模型而不是直接针对关系数据库编程的数据应用程序。  
  
 [WCF Data Services 4.5](/dotnet/framework/data/wcf/index)  
 介绍如何使用[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]部署 web 或 intranet 上的数据服务实现[开放数据协议 (OData)](http://go.microsoft.com/fwlink/?LinkID=182204)。  
  
 [Office 解决方案中的数据](/office-dev/office-dev/data-in-office-solutions)  
 包含指向这些主题介绍了数据在 Office 解决方案中的工作方式。 这包括有关面向架构的编程、 数据缓存和服务器端数据访问的信息。  
  
 [LINQ（语言集成查询）](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 描述内置于 C# 和 Visual Basic 和查询关系数据库、 XML 文档、 数据集和内存中集合的常见模型的查询功能。
  
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)  
 讨论 XML 数据，调试 XSLT，.NET Framework XML 功能，使用和 XML 查询的体系结构。  
  
 [XML 文档和数据](/dotnet/standard/data/xml/index)  
 概述了对 .NET Framework 中的 XML 文档和数据有用的一组全面、集成的类。