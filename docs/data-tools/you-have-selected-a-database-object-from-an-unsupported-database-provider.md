---
title: "选择了的数据库对象的不受支持的数据库提供程序从 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 05e638be5cc11f66052e5a1f6116e7205b824106
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您从不支持的数据库提供程序选择了数据库对象
O/R 设计器支持用于 SQL Server 仅.NET Framework 数据提供程序 (<xref:System.Data.SqlClient>)。 尽管你可以单击**确定**并继续使用来自不受支持的数据库提供程序的对象，你可能会在运行时遇到意外的行为。  
  
> [!NOTE]
>  仅支持使用用于 SQL Server 的 .NET Framework 数据提供程序的数据连接。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
- 单击“确定”。

   你可以继续设计映射到使用不支持的数据库提供程序的连接的实体类。 使用不支持的数据库提供程序时，可能遇到意外行为。  
  
     - 或 -  
  
- 单击**取消**。

   操作停止。 创建或使用采用了用于 SQL Server 的 .NET Framework 提供程序的数据连接。  
  
## <a name="see-also"></a>请参阅
[O/R 设计器消息](../data-tools/o-r-designer-messages.md)  
[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)