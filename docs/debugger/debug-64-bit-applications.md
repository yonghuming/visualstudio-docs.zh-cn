---
title: "调试 64 位应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "调试 [Visual Studio]，64 位"
  - "64 位调试"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试 64 位应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以调试运行于本地计算机或远程计算机上的 64 位应用程序。  
  
 若要调试在远程计算机上运行的 64 位应用程序，请参阅 [远程调试](../debugger/remote-debugging.md)。  
  
 若要在本地调试 64 位应用程序，Visual Studio 将使用 64 位辅助进程 \(msvsmon.exe\) 执行不能在 32 位 Visual Studio 进程内执行的低级别操作。  
  
 使用 .NET Framework 3.5 或更早版本的 64 位进程不支持混合模式调试。  
  
## 调试 64 位应用程序  
 若要尝试调试 64 位应用程序：  
  
1.  创建一个 Visual Studio 解决方案，例如 C\# 控制台应用程序。  
  
2.  使用配置管理器将配置设置为 64 位。 有关详细信息，请参阅[如何：配置项目以面向目标平台](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
3.  此时将启动 64 位版本的远程调试器 \(msvsmon.exe\)。 只要使用 64 位配置的解决方案处于打开状态，它就会运行。  
  
4.  开始调试。 这与使用 32 位配置时应该具有相同的体验。 如果出现错误，请参阅下面的“疑难解答”一节。  
  
## 64 位调试疑难解答  
 可能会出现一条错误信息：“64 位调试操作所花费的时间超出了预期。” 在这种情况下，则说明 Visual Studio 已向 64 位版本的 msvsmon.exe 发送请求，返回该请求的结果花费了较长的时间。  
  
 出现此错误的主要原因有两个：  
  
-   你的计算机上所安装的网络安全软件导致网络堆栈不可靠，并且该网络安全软件已删除通过 localhost 的数据包。 请尝试禁用全部的网络安全软件，然后查看该问题是否解决。 如果问题解决，那么请发送报告给你的网络安全软件供应商，说明该软件正在干扰 localhost 通信。  
  
-   你正遇到挂起或 Visual Studio 性能问题。 如果该问题定期发生，你可收集 Visual Studio \(devenv.exe\) 和辅助进程 \(msvsmon.exe\) 的转储并将其发送给 Microsoft。 有关报告问题的详细信息，请参阅 [如何报告 Visual Studio 的问题](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md)。  
  
## 请参阅  
 [64 位应用程序](../Topic/64-bit%20Applications.md)   
 [配置 64 位的程序](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Visual Studio IDE 64 位支持](../ide/visual-studio-ide-64-bit-support.md)   
 [使用转储文件调试应用程序崩溃和挂起](../debugger/using-dump-files.md)   
 [远程调试](../debugger/remote-debugging.md)