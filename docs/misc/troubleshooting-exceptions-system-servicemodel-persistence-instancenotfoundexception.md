---
title: "关于异常的疑难解答：System.ServiceModel.Persistence.InstanceNotFoundException | Microsoft Docs"
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
  - "InstanceNotFoundException 异常"
  - "System.ServiceModel.Persistence.InstanceNotFoundException 异常"
ms.assetid: e3905352-dff0-41d4-b970-8e1b26d85a83
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ServiceModel.Persistence.InstanceNotFoundException
当出现以下情况时，将引发 <xref:System.ServiceModel.Persistence.InstanceNotFoundException> 异常：  
  
-   在已经标记为完成的持久性服务实例上执行操作。  
  
-   <xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory> 创建的持久性提供程序尝试锁定、解除锁定或以其他方式处理数据库中不包含的状态数据。  
  
## 请参阅  
 <xref:System.ServiceModel.Persistence.InstanceNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)