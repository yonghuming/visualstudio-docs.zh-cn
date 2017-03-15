---
title: "关于异常的疑难解答：System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
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
  - "ServiceBusyException 异常"
  - "System.IdentityModel.Selectors.ServiceBusyException 异常"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IdentityModel.Selectors.ServiceBusyException
将引发 <xref:System.IdentityModel.Selectors.ServiceBusyException> 异常以指示 CardSpace 服务正在忙于处理其他的请求。 CardSpace 不会对请求进行排队，并且一次只可以服务一个请求。  
  
 确定是否正在运行另一个 CardSpace 实例。 如果另一个实例正在运行，请通过从任务管理器中停止 icardagt.exe 进程来结束正在运行的实例。  
  
## 请参阅  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)