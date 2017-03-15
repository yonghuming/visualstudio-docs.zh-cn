---
title: "错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器正以其他用户身份运行 | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "anyuser 选项"
  - "-anyuser 选项"
  - "msvsmon.exe"
  - "远程调试监视器"
  - "远程调试, 远程调试监视器"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 错误：远程计算机上的 Microsoft Visual Studio 远程调试监视器正以其他用户身份运行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当尝试执行远程调试时，您可能会收到如下错误信息：  
  
 远程计算机上的“Microsoft Visual Studio 远程调试监视器”正在以其他用户身份运行。  
  
## 原因  
 当您正在“无身份验证”模式下进行调试，而启动 msvsmon 的用户不是运行 Visual Studio 的用户时，会出现此消息。  
  
## 解决方案  
 最安全也是最好的解决方案是，以与运行 Visual Studio 的相同用户帐户运行远程调试监视器 \(msvsmon.exe\)。  如果无法做到这一点，则可以在远程调试监视器的**“选项”**对话框中选中**“允许任何用户进行调试”**选项，使用其他用户帐户运行远程调试监视器。  
  
> [!CAUTION]
>  授予其他用户进行连接的权限可能会导致意外地连接到错误的远程调试会话。  以**“无身份验证”**模式进行调试从来都不是安全的，应该谨慎使用。  
  
 有关详细信息，请参阅[启动远程调试监视器](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md)。  
  
## 请参阅  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [远程调试](../debugger/remote-debugging.md)