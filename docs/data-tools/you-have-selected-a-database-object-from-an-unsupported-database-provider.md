---
title: "您从不支持的数据库提供程序选择了数据库对象 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 您从不支持的数据库提供程序选择了数据库对象
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)]（[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]）仅支持用于 SQL Server 的 .NET Framework 数据提供程序 \(<xref:System.Data.SqlClient>\)。虽然您可以单击**“确定”**并继续使用来自不支持的数据库提供程序的对象，但在运行时可能遇到意外行为。  
  
> [!NOTE]
>  仅支持使用用于 SQL Server 的 .NET Framework 数据提供程序的数据连接。  
  
### 更正此错误  
  
-   单击**“确定”**，继续设计映射到使用不支持的数据库提供程序的连接的实体类。使用不支持的数据库提供程序时，可能遇到意外行为。  
  
     \- 或 \-  
  
-   单击**“取消”**。  
  
     操作停止。创建或使用采用了用于 SQL Server 的 .NET Framework 提供程序的数据连接。  
  
## 请参阅  
 [对象关系设计器（O\/R 设计器）](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [.NET Framework 数据提供程序](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)