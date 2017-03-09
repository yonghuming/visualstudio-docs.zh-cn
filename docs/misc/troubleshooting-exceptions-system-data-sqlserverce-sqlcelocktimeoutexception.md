---
title: "关于异常的疑难解答：System.Data.SqlServerCe.SqlCeLockTimeoutException | Microsoft Docs"
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
  - "SqlCeLockTimeoutException 异常"
  - "System.Data.SqlServerCe.SqlCeLockTimeoutException 异常"
ms.assetid: 81be7a69-f343-48f0-b94b-c6018df833cf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.SqlServerCe.SqlCeLockTimeoutException
如果已经达到锁定超时并且 SQL Server Compact 在等待锁的过程中超时，则会引发 `System.Data.SqlServerCe.SqlCeLockTimeoutException` 异常。 锁定超时的默认值是 2000 毫秒。 有关详细信息，请参阅 [SQL Server Compact 3.5 类库](http://go.microsoft.com/fwlink/?LinkID=102595)。  
  
## 请参阅  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)