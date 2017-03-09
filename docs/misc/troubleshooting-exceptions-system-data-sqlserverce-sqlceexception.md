---
title: "关于异常的疑难解答：System.Data.SqlServerCe.SqlCeException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Data.SqlServerCe.SqlCeException 异常"
  - "SqlCeException 异常"
  - "SqlServerCe.SqlCeException 异常"
ms.assetid: b0414ab9-94f1-48cc-a2ee-763c005150d5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.SqlServerCe.SqlCeException
当基础提供程序从 SQL Server Compact 数据源返回警告或错误时，将引发 `System.Data.SqlServerCe.SqlCeException` 异常。 有关此错误的原因的详细信息，请参阅 MSDN 网站上的 [SQL Server Compact 版本错误](http://msdn2.microsoft.com/library/ms171849.aspx)。  
  
## 备注  
 `System.Data.SqlServerCe.SqlCeException` 始终至少包含一个 `System.Data.SqlServerCe.SqlCeError` 实例。 无法继承此类。  
  
 有关详细信息，请参阅 [SQL Server Compact 3.5 类库](http://go.microsoft.com/fwlink/?LinkID=102595)。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)