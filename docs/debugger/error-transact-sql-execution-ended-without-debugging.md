---
title: "错误： TRANSACT-SQL 执行结束，而不进行调试 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db04460c57dd4ade94154fa1a884477452ee4108
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>错误：Transact-SQL 执行未经调试便已结束
当尝试调试 Transact-SQL 或 SQLCLR 过程而调试器未从 SQL Server 接收调试消息时，会发生此错误。  
  
 这可能是由于网络问题或 SQL Server 上的问题造成的，但是可能性最大的原因是权限问题。  
  
 这涉及到两种帐户：  
  
-   应用程序帐户是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 运行时所用的用户帐户。  
  
-   连接帐户是用于建立到 SQL Server 的连接的标识。 这不一定是该连接使用 SQL 身份验证时 Visual Studio 运行所使用的标识。  
  
 SQL 调试要求应用程序帐户必须与连接帐户匹配或者是系统管理员。  
  
 如果正使用某个类似于 sa 的 SQL 登录，则该应用程序帐户在 SQL Server 上必须设置为系统管理员。 默认情况下，运行 SQL server 的计算机上的管理员是 SQL Server 系统管理员。  
  
 若要纠正此错误，可能需要：  
  
-   验证权限设置。 有关详细信息，请参阅[如何： 为调试中设置 SQL Server 权限](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
-   如果设置正确，请确保 SQL 调试也正确。  
  
-   请咨询网络或数据库管理员。  
  
## <a name="see-also"></a>另请参阅  
 [设置 SQL 调试](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [如何： 为调试设置 SQL Server 权限](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)   
 [远程调试](../debugger/remote-debugging.md)