---
title: "将 SQL Server 与针对 Visual Studio 的 R 工具集成 | Microsoft Docs"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 919dfc34-234a-489e-91bf-74a4cefae26c
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 44ae1fd825997ff5eab1448ebd86f88a130172a1
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


# <a name="working-with-sql-server-and-r"></a>使用 SQL Server 和 R

针对 Visual Studio 的 R 工具 (RTVS) 利用 Visual Studio 对 SQL Server 出色的支持，让数据科学家更容易使用 SQL 数据库，即创建运行的 SQL 查询以及处理存储过程。

> [!Note]
> 若要配合使用 SQL 和 R，必须安装 SQL Server 数据工具：
> - Visual Studio 2017：运行 Visual Studio 安装程序并选择数据存储和处理工作负载，其中包括 SQL Server 数据工具。
> - Visual Studio 2015：按照[下载 SQL Server 数据工具](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)上的说明操作。

以下视频（3 分 03 秒）简要介绍了 SQL Server 和 R：

<iframe width="560" height="315" src="https://www.youtube.com/embed/n4AYr0QIwdQ" frameborder="0" allowfullscreen></iframe>

## <a name="creating-and-running-sql-queries"></a>创建并运行 SQL 查询

RTVS 支持将 SQL 查询添加到 R 项目，允许用户在单独的上下文中以迭代方式开发 SQL 查询，直到获得要想要结果。

若要添加 SQL 查询文件，请在解决方案资源管理器中右键单击项目，选择“添加”>“新项...”，然后选择“SQL 查询”文件类型：

![向项目添加“SQL 查询”项](~/docs/rtvs/media/sql-add-item.png)

此时 Visual Studio 的 Transact-SQL 编辑器打开该文件，该编辑器可为 SQL 提供完整的 IntelliSense 及运行查询的功能。 但若要使用这些功能，需使用编辑器工具栏中的连接按钮连接到数据库，或只需尝试运行查询（按 Ctrl+Shift+E 也可进行选择）。 无论使用哪种方法，此时都会弹出“连接”对话框：

![“SQL 连接”对话框](~/docs/rtvs/media/sql-connection-dialog.png)

建立连接后，即可运行查询并查看结果：

![SQL 窗口查询结果](~/docs/rtvs/media/sql-query-results.png)

Transact-SQL 编辑器支持其他各种功能，例如查看查询的执行计划，查看查询调试器。Transact-SQL 编辑器中还有许多其他功能可供使用。 有关详细信息，请参阅[使用 Transact-SQL 编辑器编辑和执行脚本](https://msdn.microsoft.com/library/hh272706.aspx)。

## <a name="working-with-sql-server-stored-procedures"></a>处理 SQL Server 存储过程

通过 [SQL Server R 服务](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services)（SQL Server 2016 及更高版本）可从 T-SQL 存储过程嵌入和运行 R 代码。 这意味着用户可运行 R 代码 SQL Server 计算机，处理从 SQL 查询返回的数据，并生成可由 SQL 进一步处理的或返回给客户端的 SQL 结果集。

在单个 SQL 语句中结合 SQL和 R 代码时，结合过程不易操作且容易出错，RTVS 简化了该过程，如以下各部分所述：

- [添加数据库连接](#add-a-database-connection)
- [编写和测试 SQL 存储过程](#write-and-test-a-sql-stored-procedure)
- [发布 SQL 存储过程](#publish-a-sql-stored-procedure)

以下视频（6 分 09 秒）还粗略介绍了这些功能：

<iframe width="560" height="315" src="https://www.youtube.com/embed/dFKIT2OitWQ" frameborder="0" allowfullscreen></iframe>

### <a name="add-a-database-connection"></a>添加数据库连接

1. 选择“R 工具”>“数据”>“添加数据库连接”，弹出“连接属性”对话框，在其中可以指定数据源的名称（本案例中为 SQL Server）、服务器名称、身份验证模式和数据库名称。 关闭对话框前，可选择“测试连接”验证输入。
 
    ![“SQL 连接”对话框](~/docs/rtvs/media/sql-connection-string-dialog.png)

1. 在通过有效连接选择“确定”后，Visual Studio 会在新 `settings.R` 文件中生成一个名为 `dbConnection` 的连接字符串。 RTVS 会自动寻源（运行）此文件，因此可立即使用 R 脚本的连接：

![SQL Settings.R 文件](~/docs/rtvs/media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>编写和测试 SQL 存储过程

若要添加新 SQL 存储过程，请右键单击项目，选择“添加”>“新项...”，从模板列表选择“使用 R 的 SQL 存储过程”，命名文件（本示例中名称为 `StoredProcedure.R`），然后选择“确定”。
 
RTVS 会为存储过程创建三个文件，为 R 代码创建 `.R` 文件，为 SQL 代码创建 `.Query.sql` 文件，以及结合这两个文件的 `.Template.sql` 文件。 后两者会作为 `.R` 文件的子文件出现在解决方案资源管理器中：

![使用 R 的 SQL 存储过程的解决方案资源管理器展开视图](~/docs/rtvs/media/sql-solution-explorer-expanded.png)

`StoredProcedure.R`（在本例中）是编写 R 代码的位置。 默认内容如下：

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

简言之，代码接收一个名为 `InputDataSet` 的 R 数据帧，并将其结果返回到 `OutputDataSet`，模板代码只会将输入复制到输出。

> [!Note]
> 在调用 `sp_execute_external_script` 系统存储过程时，这些数据帧的名称由 `@input_data_1_name` 和 `@output_data_1_name` 参数控制。 有关此调用约定的设计及其用法示例的更多详细信息，请参阅 [sp_execute_external_script (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)。

注释中生成的其他代码是一个小测试脚本，该脚本使用 [RODBC 包](https://cran.r-project.org/web/packages/RODBC/index.html)将 SQL 语句传输到 SQL Server 并运行，然后取回其结果集作为 R 数据帧。 可取消注释此测试代码，根据从 SQL Server 获取的结果集交互编写 R 代码。

在 `StoredProcedure.Query.sql` 可以编写和测试 SQL 查询，以生成 `InputDataSet` 数据。 因为这是一个 `.sql` 文件，所以可使用所有 Transact-SQL 编辑器功能。

对 SQL 代码感到满意后，只需将 `.sql` 文件拖放到 `.R` 文件打开的编辑器中，即可轻松地将该代码与 `StoredProcedure.R` 中的 R 代码集成。 在下图中，`StoredProcedure.Query.sql` 已被拖到 `sqlQuery(channel, )` 中逗号后的位置：

![将 SQL 文件读入 R 字符串变量](~/docs/rtvs/media/sql-reference-sql-file-from-r.png)

如图所示，这个简单的步骤可自动生成 R 代码，打开 `.sql` 文件，将其内容读入字符串，并将其传递给 RODBC 包以发送到 SQL Sever。

准备就绪后，你便可以交互编写 R 代码，按需处理 `InputDataSet` 数据帧。 请记住，只能在编辑器中选择 R 代码，然后按 Ctrl+Enter 将其发送到[交互窗口](interactive-repl.md)。

最后，`StoredProcedure.Template.sql` 会包含用于生成 SQL 存储过程的模板：

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_` 占位符由 `StoredProcedure.R` 的内容替代。
- `_INPUT_QUERY_` 占位符由 `StoredProcedure.Query.sql` 的内容替代。
- 用户需编辑 `WITH RESULT SETS` 子句，描述从存储过程返回的结果集的架构。 特别指出要返回存储过程调用者的 `OutputDataSet` 数据帧的列。 

例如，对于以下查询：

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

可使用以下 `WITH RESULT SETS` 子句来指定返回值的数据类型：

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>发布 SQL 存储过程

1. 选择“R工具”>“数据”>“使用选项发布...”菜单命令。
1. 在出现的对话框中，将“发布到:”更改为“数据库”，指定目标，选择“发布”，然后 RTVS 会生成和发布存储过程：

    ![“发布存储过程”对话框](~/docs/rtvs/media/sql-publish-with-options.png)

1. 若要发布项目中所有的存储过程，还可使用“R 工具”>“数据”>“发布存储过程”命令。右键单击解决方案资源管理器中的项目也可使用该命令。

> [!Tip]
> 如果在 Visual Studio 中打开了 SQL Server 对象资源管理器，则在数据库的“可编程性”>“存储过程”文件夹也会显示已发布的存储过程。 另外，通过右键单击并选择“执行过程”，或者从 `.sql` 查询窗口交互调用，也可以从对象资源管理器执行该操作。

