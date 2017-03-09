---
title: "关于异常的疑难解答：System.Net.WebException | Microsoft Docs"
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
  - "WebException 类"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Net.WebException
通过可插协议访问网络发生错误时，会引发 <xref:System.Net.WebException> 异常。  
  
## 相关提示  
 **检查异常的 Response 属性以确定请求失败的原因。**  
 如果 <xref:System.Net.WebException> 异常是由 <xref:System.Net.WebRequest> 类的派生类引发的，则 <xref:System.Net.WebException.Response%2A> 属性向应用程序提供 Internet 响应。  
  
 **检查异常的 Status 属性以确定请求失败的原因。**  
 异常的 <xref:System.Net.WebException.Status%2A> 属性提供错误的状态信息。 有关详细信息，请参阅<xref:System.Net.WebExceptionStatus>。  
  
 **如果单步执行 XML Web services 时超时，请将 XML Web services 调用的超时值设置为无限。**  
 有关详细信息，请参阅[错误：调试 Web 服务时超时](../debugger/error-timeout-while-debugging-web-services.md)。  
  
## 请参阅  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [如何：使用 WebRequest 类发送数据](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [如何使用 WebRequest 类请求数据](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [如何：检索与 WebRequest 匹配的特定于协议的 WebResponse](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)