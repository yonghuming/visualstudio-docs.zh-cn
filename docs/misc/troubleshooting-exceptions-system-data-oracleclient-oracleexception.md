---
title: "关于异常的疑难解答：System.Data.OracleClient.OracleException | Microsoft Docs"
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
  - "OracleException 类"
  - "Oracle"
  - "异常, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.OracleClient.OracleException
当 Oracle 数据库或用于 Oracle 的 .NET Framework 数据提供程序返回一个警告或错误时，会生成一个 <xref:System.Data.OracleClient.OracleException> 异常。  
  
## 相关提示  
 **验证您是否在使用有效的凭据进行连接。**  
 确保您提供的凭据有效。  
  
 **验证服务器名称是否正确，服务器是否正在运行。**  
 确保使用了正确的服务器名称，且该服务器可达。  
  
## 备注  
 每当 <xref:System.Data.OracleClient.OracleDataAdapter> 遇到服务器生成的错误时，都将引发此异常。  
  
 如果错误的严重程度太高，服务器可能会关闭 <xref:System.Data.OracleClient.OracleConnection>。 但是，用户可以重新打开连接并继续操作。  
  
## 请参阅  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)