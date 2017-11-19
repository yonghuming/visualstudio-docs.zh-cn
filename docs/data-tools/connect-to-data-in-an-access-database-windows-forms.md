---
title: "连接到 Access 数据库 （Windows 窗体） 中的数据 |Microsoft 文档"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 1f67a87f4a704d3f76ccddba62112983c058a9f3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>连接到 Access 数据库 （Windows 窗体） 中的数据
可以通过使用 Visual Studio 连接到 Access 数据库 （.mdf 文件或.accdb 文件）。 在定义此连接后，数据将显示在**数据源**窗口。 可从该位置将表或视图拖动到窗体上。   
  
## <a name="prerequisites"></a>先决条件  
 若要使用这些过程，你需要 Windows 窗体应用程序项目和 Access 数据库 （.accdb 文件） 或 Access 2000-2003年数据库 （.mdb 文件）。 按照与你的文件类型对应的过程操作。  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>创建.accdb 文件的数据集  
 你可以连接到使用以下过程通过 Access 2013、 Office 365、 Access 2010 或 Access 2007 创建的数据库。  
  
#### <a name="to-create-the-dataset"></a>创建数据集  
  
1.  打开你想要将数据连接的 Windows 窗体应用程序。  
  
2.  上**视图**菜单上，选择**其他窗口** > **数据源**。  
  
     ![查看其他 Windows 数据源](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  在 **“数据源”** 窗口中，单击 **“添加新数据源”**。  

     **数据源配置向导**打开。  
  
4.  选择**数据库**上**选择数据源类型**页上，然后选择**下一步**。  
  
5.  选择**数据集**上**选择数据库模型**页上，然后选择**下一步**。  
  
6.  上**选择你的数据连接**页上，选择**新连接**来配置新的数据连接。  

     **添加连接**对话框随即打开。  
  
7.  选择**更改**按钮旁边**数据源**文本框。

     **更改数据源**对话框随即打开。  
  
8.  在数据源的列表中，选择**\<其他\>**。 在**数据提供程序**下拉列表中，选择**OLE DB 的.NET Framework 数据提供程序**，然后选择**确定**。  

9. 返回**添加连接**对话框中，选择**Microsoft Office 12.0 Access 数据库引擎 OLE DB 提供程序**从**OLE DB 访问接口**下拉列表。  
  
     ![OLE DB 提供程序 Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  

     > [!NOTE]
     >  如果看不到**Microsoft Office 12.0 Access 数据库引擎 OLE DB 提供程序**OLE DB 提供程序下拉列表中，你可能需要安装[2007 Office System 驱动程序： 数据连接组件](https://www.microsoft.com/download/confirmation.aspx?id=23734)。
  
9. 在**服务器或文件名称**文本框中，指定的路径和文件你想要连接到的.accdb 文件的名称，然后选择**确定**。 (如果数据库文件具有用户名和密码，指定它们，然后选择**确定**。)    
  
10. 选择**下一步**上**选择你的数据连接**页。  

     你可能会收到一个对话框，告诉你数据文件不在当前项目。 选择**是**或**否**。
  
11. 选择**下一步**上**将连接字符串保存到应用程序配置文件**页。  
  
12. 展开**表**上的节点**选择数据库对象**页。  
  
13. 选择任何表或视图，您想在你的数据集，然后选择**完成**。  
  
     数据集添加到你的项目，而表和视图显示在**数据源**窗口。  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>创建数据集为.mdb 文件  
 通过运行创建数据集**数据源配置向导**。  
  
#### <a name="to-create-the-dataset"></a>创建数据集  
  
1.  打开你想要将数据连接的 Windows 窗体应用程序。  
  
2.  上**视图**菜单上，选择**其他窗口** > **数据源**。  
  
     ![查看其他 Windows 数据源](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  在 **“数据源”** 窗口中，单击 **“添加新数据源”**。  

     **数据源配置向导**打开。
  
4.  选择**数据库**上**选择数据源类型**页上，然后选择**下一步**。  
  
5.  选择**数据集**上**选择数据库模型**页上，然后选择**下一步**。  
  
6.  上**选择你的数据连接**页上，选择**新连接**来配置新的数据连接。  
  
7.  如果数据源不是**Microsoft Access 数据库文件 (OLE DB)**，选择**更改**以打开**更改数据源**对话框，选择**Microsoft访问数据库文件**，然后选择**确定**。  
  
8.  在**数据库文件名**，指定的路径和你想要连接到，然后选择的.mdb 文件的名称**确定**。  
  
     ![添加连接访问数据库文件](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. 选择**下一步**上**选择你的数据连接**页。  
  
10. 选择**下一步**上**将连接字符串保存到应用程序配置文件**页。  
  
11. 展开**表**上的节点**选择数据库对象**页。  
  
12. 选择任何表或视图，您想在你的数据集，然后选择**完成**。  
  
     数据集添加到你的项目，而表和视图显示在**数据源**窗口。  
  
## <a name="security"></a>安全性  
 存储敏感信息（如密码）会影响应用程序的安全性。 若要控制对数据库的访问，一种较为安全的方法是使用 Windows 身份验证（也称为集成安全性）。 有关详细信息，请参阅[保护连接信息](/dotnet/framework/data/adonet/protecting-connection-information)。  
  
## <a name="next-steps"></a>后续步骤  
 你刚刚创建的数据集现已推出**数据源**窗口。 现在，你可以执行任何以下任务：  
  
-   中选择项目**数据源**窗口并将它们拖到窗体 (请参阅[绑定 Windows 窗体控件添加到 Visual Studio 中的数据](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md))。  
  
-   打开中的数据源**数据集设计器**可以添加或编辑组成数据集的对象。  
  
-   添加到的验证逻辑<xref:System.Data.DataTable.ColumnChanging>或<xref:System.Data.DataTable.RowChanging>的数据集中数据表的事件 (请参阅[验证数据集中的数据](../data-tools/validate-data-in-datasets.md))。  
  
## <a name="see-also"></a>请参阅
[添加连接](../data-tools/add-new-connections.md)
