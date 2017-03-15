---
title: "关于异常的疑难解答：System.Net.CookieException | Microsoft Docs"
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
  - "CookieException 类"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Net.CookieException
当向一个 Cookie 容器添加 Cookie 发生错误时会引发 <xref:System.Net.CookieException> 异常。  
  
## 相关提示  
 **确保 Cookie 大小不会超出 Cookie 容器所允许的最大值。**  
 当尝试向 <xref:System.Net.Cookie> 中添加一个长度大于 <xref:System.Net.CookieContainer.MaxCookieSize%2A> 的 <xref:System.Net.CookieContainer> 时会引发此异常。 默认的最大 Cookie 大小为 4096 字节。  
  
 **当为一个 Cookie 设置 Name 属性时，应确保该值不是 null 引用或空字符串。**  
 在使用 <xref:System.Net.Cookie.Name%2A> 类的实例之前必须初始化 <xref:System.Net.Cookie> 属性。 以下字符是保留的并且不能用于此特性值：等号、分号、逗号、换行符 \(\\n\)、回车符 \(\\r\)、制表符 \(\\t\)。 货币符号 \($\) 不能作为第一个字符。  
  
 **当为 Cookie 设置 Port 属性时，应确保该值有效并括在双引号中。**  
 <xref:System.Net.Cookie.Port%2A> 特性限制可以将 Cookie 发送到的端口。 默认值表示没有限制。 设置该属性为空字符串 \(""\) 会将端口限制为在 HTTP 响应中使用的端口。 否则该值必须是一个用引号括起来的字符串，其中包含以逗号分隔的端口值。  
  
 **当为 Cookie 设置 Value 属性时，应确保该值不为 null。**  
 以下字符是保留的并且不能用于此属性：分号、逗号。  
  
## 请参阅  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)