---
title: "错误：调试 Web 服务时超时 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, Web 应用程序错误"
  - "XML Web services, 调试时超时"
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：调试 Web 服务时超时
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在从调用代码单步执行 XML Web service 时，调用有时可能会超时，结果是您无法继续调试。  您可能会看到下面这样的错误信息。  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## 解决方案  
 若要避免此问题，请将 XML Web service 调用的超时值设置为无限大，如下面的示例所示：  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## 请参阅  
 [调试 Web 应用程序：错误和疑难解答](../debugger/debugging-web-applications-errors-and-troubleshooting.md)