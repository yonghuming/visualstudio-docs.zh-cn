---
title: "CA2100： 检查 SQL 查询是否存在安全漏洞 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c28bf4d7162a7b646653ff1833067d47e7ff574d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100：检查 SQL 查询中是否有安全漏洞
|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|类别|Microsoft.Security|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 一个方法设置<xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>通过使用一个字符串，该方法生成从一个字符串自变量的属性。  
  
## <a name="rule-description"></a>规则说明  
 此规则假定字符串参数中包含用户输入。 基于用户输入生成的 SQL 命令字符串易于受到 SQL 注入式攻击。 在 SQL 注入攻击，恶意用户提供将在尝试损坏或未经授权的访问到基础数据库更改设计的查询的输入。 典型的方法包括注入单个引号或单引号，这是 SQL 文本字符串分隔符;两个短划线，表示 SQL 注释;和一个分号，这表明，新的命令如下所示。 如果用户输入必须是属于该查询，使用以下命令，其中一个顺序列出的有效性，以减少攻击的风险。  
  
-   使用存储的过程。  
  
-   使用参数化的命令字符串。  
  
-   生成的命令字符串之前，请验证类型和内容的用户输入。  
  
 以下[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]类型实现<xref:System.Data.IDbCommand.CommandText%2A>属性，或者提供通过使用字符串自变量将属性设置的构造函数。  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 和 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 和 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 和 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](https://msdn.microsoft.com/library/system.data.sqlserverce.sqlcecommand.aspx)和[System.Data.SqlServerCe.SqlCeDataAdapter](https://msdn.microsoft.com/library/system.data.sqlserverce.sqlcedataadapter.aspx)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 和 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 请注意显式或隐式使用 ToString 方法的类型时违反了此规则来构造查询字符串。 下面是一个示例。  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 违反了规则，因为恶意用户可以重写 tostring （） 方法。  
  
 隐式使用 ToString 时也被违反规则。  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使用参数化的查询。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果命令文本不包含任何用户输入。  
  
## <a name="example"></a>示例  
 下面的示例演示一种方法， `UnsafeQuery`，了违反规则和方法， `SaferQuery`，通过使用参数化的命令字符串满足该规则。  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [安全性概述](/dotnet/framework/data/adonet/security-overview)