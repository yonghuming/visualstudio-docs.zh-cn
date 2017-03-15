---
title: "CA2100：检查 SQL 查询中是否有安全漏洞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100：检查 SQL 查询中是否有安全漏洞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## 原因  
 方法通过使用基于它的字符串参数生成的字符串来设置 <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> 属性。  
  
## 规则说明  
 此规则假定字符串参数中包含用户输入。  基于用户输入生成的 SQL 命令字符串易于受到 SQL 注入式攻击。  在 SQL 注入式攻击中，恶意用户提供将更改查询设计的输入，以尝试破坏基础数据库或获取对基础数据库的未经授权的访问权限。  典型的方法包括注入单引号或省略号（它们都是 SQL 文本字符串分隔符）、两个短划线（表示 SQL 注释）和一个分号（指示后面有新命令）。  如果用户输入必须是查询的一部分，请使用下面按有效性顺序列出的方法之一来降低攻击风险。  
  
-   使用存储过程。  
  
-   使用参数化命令字符串。  
  
-   在生成命令字符串之前针对类型和内容验证用户输入。  
  
 下面的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类型实现 <xref:System.Data.IDbCommand.CommandText%2A> 属性，或提供可通过使用字符串参数来设置该属性的构造函数。  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 和 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 和 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 和 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) 和 [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 和 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 请注意，一个类型的 ToString 方法被用来显式或隐式构造查询字符串时，会违反此规则。  下面是一个示例。  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 因为恶意用户可以重写 ToString \(\) 方法，会违反此规则。  
  
 隐式使用 ToString 时也会违反此规则。  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请使用参数化查询。  
  
## 何时禁止显示警告  
 如果命令文本中不包含任何用户输入，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 下面的示例演示与该规则冲突的方法 `UnsafeQuery` 以及通过使用参数化命令字符串来满足该规则的方法 `SaferQuery`。  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## 请参阅  
 [安全性概述](../Topic/Security%20Overview2.md)