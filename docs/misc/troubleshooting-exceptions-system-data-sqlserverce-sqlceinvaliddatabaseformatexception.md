---
title: "关于异常的疑难解答：System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SqlCeInvalidDatabaseFormatException 异常"
  - "System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException 异常"
ms.assetid: f5ca1f40-4619-4523-807e-d5b20bfb05b0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException
当 SQL Server Compact 打开在该产品的早期版本中创建的数据库文件时，将发生 `System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException` 异常。  
  
## 备注  
 可以使用 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 或 API `System.Data.SqlServerCe.SqlCeEngine.Upgrade` 更新数据库文件。  
  
 有关详细信息，请参阅 [SQL Server Compact 3.5 类库](http://go.microsoft.com/fwlink/?LinkID=102595)。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)