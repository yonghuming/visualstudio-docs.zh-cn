---
title: "关于异常的疑难解答：System.Data.SqlClient.SqlException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SqlException 类"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.SqlClient.SqlException
当 SQL Server 返回警告或错误时，将生成 <xref:System.Data.SqlClient.SqlException> 异常。  
  
## 相关提示  
 **验证您是否在使用有效的凭据进行连接。**  
 确保您提供的凭据有效。 有关更多信息，请参见[How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)。  
  
 **验证服务器名称是否正确，服务器是否正在运行。**  
 确保使用了正确的服务器名称，且该服务器可达。  
  
### 备注  
 当用于 SQL Server 的 .NET Framework 数据提供程序遇到服务器生成的错误时，将引发此异常。  
  
 严重级别为 10 或以下的消息为信息性的，并指示问题是由用户输入的信息中的错误导致的。 严重级别为 11 到 16 的消息是用户生成的，并可由用户更正。 严重级别为 17 到 25 的消息指示存在软件或硬件错误。 当发生级别为 17、18 或 19 的错误时，虽然可能无法执行某一特定语句，但仍然可以继续工作。  
  
 当严重级别为 19 或以下时，<xref:System.Data.SqlClient.SqlConnection> 将保持打开状态。 当严重度等于或大于 20 时，服务器通常会关闭 <xref:System.Data.SqlClient.SqlConnection>。 但是，用户可以重新打开连接并继续操作。 最后两种情况下，执行该命令的方法将生成 <xref:System.Data.SqlClient.SqlException>。  
  
 有关 SQL Server 发送的警告和信息性消息的更多信息，请参见“SQL Server 联机丛书”中的“疑难解答”一节。  
  
## 请参阅  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)