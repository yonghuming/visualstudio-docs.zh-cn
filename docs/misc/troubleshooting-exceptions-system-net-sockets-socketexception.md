---
title: "关于异常的疑难解答：System.Net.Sockets.SocketException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "SocketException 类"
ms.assetid: 89e8194d-83b0-450f-91f5-548e5c13944d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Net.Sockets.SocketException
当网络发生错误时，<xref:System.Net.Sockets.SocketException> 和 <xref:System.Net.Sockets.Socket> 类引发 <xref:System.Net.Dns> 异常。  
  
## 相关提示  
 **检查 Errorcode 属性以确定发生该套接字错误的原因。**  
 <xref:System.Net.Sockets.SocketException> 类默认的构造函数将 <xref:System.Net.Sockets.SocketException.ErrorCode%2A> 属性设置为最后一次发生的操作系统套接字错误。  
  
## 请参阅  
 <xref:System.Net.Sockets.SocketException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [使用安全套接字层](../Topic/Using%20Secure%20Sockets%20Layer.md)