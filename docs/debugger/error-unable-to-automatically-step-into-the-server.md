---
title: "错误：无法自动单步执行服务器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "远程调试, 通知错误"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：无法自动单步执行服务器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此错误显示如下：  
  
 无法自动单步执行服务器。 在远程过程执行前调试器未得到通知  
  
 当你尝试单步执行 Web 服务时，可能发生此错误（请参阅[单步执行 XML Web services](http://msdn.microsoft.com/zh-cn/8e67de38-bf5f-41cc-a457-1b88ce63d764)）。 只要 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 未正确设置，就会发生此错误。  
  
 可能的原因有：  
  
-   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应用程序的 web.config 文件未将调试设置为“true”（请参见 [ASP.NET 应用程序中的调试模式](../debugger/how-to-enable-debugging-for-aspnet-applications.md)）。  
  
-   在安装 Visual Studio 后安装了某个版本的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]。[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 应在安装 Visual Studio 之前安装。 若要修复此问题，请使用 Window“控制面板”和“程序和功能”来修复 Visual Studio 安装。  
  
## 请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)