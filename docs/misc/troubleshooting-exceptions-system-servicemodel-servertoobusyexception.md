---
title: "关于异常的疑难解答：System.ServiceModel.ServerTooBusyException | Microsoft Docs"
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
  - "System.ServiceModel.ServerTooBusyException 异常"
  - "ServerTooBusyException 异常"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.ServiceModel.ServerTooBusyException
当服务器太忙而无法接受消息时，将引发 <xref:System.ServiceModel.ServerTooBusyException> 异常。  
  
## 备注  
 此异常派生自表示一类可恢复错误的 <xref:System.ServiceModel.CommunicationException>，这些错误可能会在终结点相互通信期间引发。 可靠的客户端和服务 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 应用程序应处理这些异常。 若要阻止 <xref:System.ServiceModel.CommunicationException> 的处理程序捕捉更为具体的 <xref:System.ServiceModel.ServerTooBusyException>，请在处理 <xref:System.ServiceModel.CommunicationException> 之前捕捉此异常。  
  
## 请参阅  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)