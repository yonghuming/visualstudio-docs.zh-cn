---
title: "适用于 c + + 的 visual Studio data tools |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: c5952c4ab8e8adac0338d406800a15a8a0b12989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-data-tools-for-c"></a>适用于 c + + 的 visual Studio data tools
你在访问数据源时，本机 c + + 通常可以提供最快的性能。 但是，不同样丰富，因为它是.NET 应用程序的工具，用于在 Visual Studio 中的 c + + 应用程序的数据。 例如，不能使用数据源窗口拖放到 c + + 设计图面上的数据源。 如果你需要对象关系图层，你将需要编写你自己，或使用第三方产品。  同样适用于数据绑定功能，尽管使用 Microsoft 基础类库的应用程序可以使用一些数据库类中的，文档和视图，以及在内存中存储数据并将其显示给用户。 有关详细信息，请参阅[Visual c + + 中的数据访问](https://msdn.microsoft.com/en-us/library/7wtdsdkh.aspx)。  
  
 若要连接到 SQL 数据库，本机 c + + 应用程序可以使用 ODBC 和 OLE DB 驱动程序和 Windows 附带的 ADO 提供程序。 这些可以连接到的所有数据库都支持这些接口。 ODBC 驱动程序是标准。 提供 OLE DB 是为了向后兼容。 这些数据技术的详细信息，请参阅[Windows 数据访问组件](https://msdn.microsoft.com/en-us/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 利用 SQL Server 2005 中的自定义功能和更高版本，使用[SQL Server Native Client](https://msdn.microsoft.com/en-us/sqlserver/aa937733)。 本机客户端还包含 SQL Server ODBC 驱动程序以及一个本机动态链接库 (DLL) 中的 SQL Server OLE DB 提供程序。 这些支持使用本机代码 Api （ODBC、 OLE DB 和 ADO） 到 Microsoft SQL Server 的应用程序。  SQL Server Native Client 随同一起 SQL Server Data Tools 安装。 编程指南是此处： [SQL Server Native Client 编程](https://msdn.microsoft.com/en-us/library/ms130892.aspx)。  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>若要从 c + + 应用程序连接到 localDB 通过 ODBC 和 SQL Native Client  
  
1.  安装 SQL Server Data Tools。  
  
2.  如果你需要连接到一个示例 SQL 数据库，下载 Northwind 数据库，并将其解压缩到新位置。  
  
3.  使用 SQL Server Management Studio 将解压缩的 Northwind.mdf 文件附加到 localDB。 SQL Server Management Studio 启动时，连接到 (localdb) \MSSQLLocalDB。  
  
     ![使用 SSMS 连接对话框](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS 连接对话框")  
  
     右键单击左窗格中中的 localdb 节点，然后选择**附加**。  
  
     ![SSMS 附加数据库](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS 附加数据库")  
  
4.  下载 ODBC Windows SDK 示例中，并将其解压缩到新位置。 此示例演示用于连接到数据库和问题查询和命令的基本 ODBC 命令。 你可以了解有关这些函数中[Microsoft 开放式数据库连接 (ODBC)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms710252\(v=vs.85\).aspx)。 当你首次加载的解决方案 （它是在 c + + 文件夹） 时，将提供 Visual Studio 升级到当前版本的 Visual Studio 的解决方案。 单击 **“是”**。  
  
5.  若要使用的本机客户端，你需要其标头文件和 lib 文件。 这些文件包含函数和特定于 SQL Server，超出 sql.h 中定义的 ODBC 函数定义。 在**项目** > **属性** > **VC + + 目录**，添加以下包含目录：  
  
 **\<系统驱动器 >: files\microsoft SQL Server\110\SDK\Include**和此库目录：  
  
 **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6.  将这些行添加 odbcsql.cpp 中。 #Define 阻止从正在编译的不相关 OLE DB 定义。  
  
    ```C++  
    #define _SQLNCLI_ODBC_  
    #include <sqlncli.h>  
    ```  
  
     请注意，此示例不实际使用的任何本机客户端功能，因此前面的步骤，则不需要为其编译和运行。 但是，项目现在配置为使用你要使用此功能。 有关详细信息，请参阅[SQL Server Native Client 编程](https://msdn.microsoft.com/en-us/library/ms130892\(v=sql.130\).aspx)。  
  
7.  指定要在 ODBC 子系统中使用的驱动程序。 此示例将作为命令行参数传递中的驱动程序连接字符串属性。 在**项目** > **属性** > **调试**，添加此命令自变量：  
  
    ```C++  
    DRIVER="SQL Server Native Client 11.0"  
    ```  
  
8.  按 F5 生成并运行该应用程序。 你应看到一个对话框会提示你输入的数据库的驱动程序中。 输入`(localdb)\MSSQLLocalDB`，并检查**使用信任连接**。 Press **OK**. 你应看到消息，指示成功的连接的控制台。 你应看到命令提示符下可以在其中键入 SQL 语句中。 下面的屏幕显示的示例查询和结果：  
  
     ![ODBC 示例查询输出](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC 示例查询输出")  
  
## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)