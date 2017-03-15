---
title: "关于异常的疑难解答：System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException 类"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Net.HttpListenerException
当处理超文本传送协议请求期间发生错误时，将引发 <xref:System.Net.HttpListenerException>。  
  
## 相关提示  
 确保尝试注册的 URI 前缀尚未被注册。  
 如果 URI 前缀已被注册，将引发此异常。  
  
 确保您的 HTTP 请求有效。  
 如果在 <xref:System.Net.HttpListener> 的初始化期间或在创建或发送对 HTTP 请求的响应时发生错误，<xref:System.Net.HttpListener> 类及其关联类将引发此异常。  
  
 如果要使用 `HttpListenerPrefixCollection.Add` 方法，请确保尚未添加该 `uriPrefix`。  
 如果另一个 <xref:System.Net.HttpListener> 已经添加了前缀 `uriPrefix`，将引发此异常。  
  
## 请参阅  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)