---
title: "选择的连接使用了不支持的数据库提供程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 选择的连接使用了不支持的数据库提供程序
在将未使用用于 SQL Server 的 .NET Framework 数据提供程序的项从**“服务器资源管理器”**\/**“数据库资源管理器”**拖动到[对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)上时，出现此消息。  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]仅支持使用用于 SQL Server 的 .NET Framework 提供程序的数据连接。只有指向 Microsoft SQL Server 或 Microsoft SQL Server 数据库文件的连接才有效。  
  
### 更正此错误  
  
-   仅当项来自于使用用于 SQL Server 的 .NET Framework 数据提供程序的数据连接时，才将其添加到 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]中。  
  
## 请参阅  
 <xref:System.Data.SqlClient>   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/zh-cn/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [.NET Framework 数据提供程序](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [演练：创建 LINQ to SQL 类（O\/R 设计器）](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [创建数据应用程序](../data-tools/creating-data-applications.md)