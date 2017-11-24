---
title: "添加新的连接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 06170174436f37713f20c708c439e79af4d90198
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2017
---
# <a name="add-new-connections"></a>添加新连接

可以测试你的连接到数据库或服务，还可以通过使用浏览数据库内容和架构，**服务器资源管理器**，**云资源管理器**，或**SQL Server 对象资源管理器**. 这些窗口的功能在某种程度上重叠。 基本差异有：

- 服务器资源管理器

   默认情况下，Visual Studio 中安装。 可以用于测试连接和查看 SQL Server 数据库、 安装，了 ADO.NET 提供程序的任何其他数据库和某些 Azure 服务。 此外显示低级别的对象，如系统性能计数器、 事件日志和消息队列。 如果数据源具有没有 ADO.NET 提供程序，它不会出现在这里，但你仍可使用它从 Visual Studio 通过以编程方式连接。

- Cloud Explorer

   为 Visual Studio 扩展手动安装此窗口，通过选择**工具**，**扩展和更新**，**联机**， **Visual Studio 应用商店**. 提供用于浏览并连接到 Azure 服务的专用的功能。

- SQL Server 对象资源管理器

   使用 SQL Server Data Tools 安装和下可见**视图**菜单。 如果看不到它存在，请转到**程序和功能**在 Control Panel 中，找到 Visual Studio，然后选择**更改**选择 SQL Server Data tools 的复选框后重新运行安装程序。 使用**SQL Server 对象资源管理器**到视图的 SQL 数据库 （如果他们有的 ADO.NET 提供程序），创建新数据库、 修改架构、 创建存储的过程、 检索连接字符串、 查看数据，等等。 具有未安装的 ADO.NET 提供程序的 SQL 数据库不会显示在这里，但你仍可连接到它们以编程方式。

## <a name="add-a-connection-in-server-explorer"></a>在服务器资源管理器添加连接

若要创建与数据库的连接，请单击**添加连接**图标**服务器资源管理器**，或右键单击**服务器资源管理器**上**数据连接**节点，然后选择**添加连接**。 从这里，你可以还连接到另一台服务器、 SharePoint 服务或一项 Azure 服务上的数据库。

![服务器资源管理器的新连接图标](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata 服务器资源管理器中新的连接图标")

这将显示**添加连接**对话框。 在这里，我们输入 SQL Server LocalDB 实例的名称。  

![添加新连接](../data-tools/media/raddata-add-new-connection-dialog.png "raddata 添加新连接对话框")  

## <a name="change-the-provider"></a>更改提供程序

如果数据源不是你所希望的内容，请单击**更改**按钮以选择新的数据源和/或新的 ADO.NET 数据提供程序。 新的提供程序可能会要求你输入凭据，具体取决于你配置的方式。

![更改 AD0.NET 数据提供程序](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata 更改 AD0.NET 数据提供程序")

## <a name="test-the-connection"></a>测试连接

在选择数据源之后，单击**测试连接**。 如果未成功，你将需要进行故障排除基于供应商的文档。

![测试连接](../data-tools/media/raddata-test-connection.png "raddata 测试连接")

如果测试成功，你就可以创建*数据源*，这是真正含义的 Visual Studio 术语*数据模型*基于基础数据库或服务。

## <a name="see-also"></a>请参阅

[适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)