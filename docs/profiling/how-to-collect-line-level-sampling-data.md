---
title: "如何：收集行级采样数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "性能工具, 行级采样"
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：收集行级采样数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

行级取样是探测器的功能，用于确定在频繁使用处理器的函数（例如具有高独占取样的函数）代码中处理器不得不花费大部分时间的位置。  
  
## 概述  
 对于行级取样，探查器会按设置的时间间隔运行程序调用堆栈，并聚合这些结果。  这些结果显示进行取样时处理器执行了哪些指令。  然后分析收集的有关独占样本的数据，以识别代码行和指令指针 \(IP\)。  
  
 行级取样适用于托管代码和本机代码。  显示此数据的性能报告包含“行”视图和“模块”视图。  
  
 字符开始\/结尾信息不可用于本机代码。  对于多行语句，行开始信息不可用于本机代码；只有行结尾信息可用。  
  
### 可用数据  
 可用行级取样数据包括以下信息：  
  
-   函数名。  
  
-   函数地址。  
  
-   行开始 – 取样代码的行号。  
  
-   行结尾 – 结尾源行号。  通常与“行开始”数据相同（一个程序语句跨多个源代码行的情况除外）。  
  
-   字符开始 – 聚合样本的开始列。  通常为 0（一行包含多个程序语句的情况除外）。  
  
-   字符结尾 – 聚合样本的结尾列。  
  
-   IP – 聚合样本所采用的地址（仅 IP 视图）。  
  
 在**“模块”**视图中，如果函数具有行级统计信息，那么这些统计信息将嵌套在每个函数下。  另外，会显示嵌套在每行下的 IP 级统计数据。  
  
### 关闭托管代码的行级取样  
 默认情况下，行级取样处于打开状态。  您可以通过执行以下一种操作来关闭托管代码的行级数据收集：  
  
-   分析之前，键入 VSPerfCLREnv \/samplelineoff。  这会同时影响应用程序和服务。  
  
     \- 或 \-  
  
-   当启动应用程序时，键入 VSPerfCmd \/lineoff \<其他参数\>.  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [对分析工具数据进行分析](../profiling/analyzing-performance-tools-data.md)