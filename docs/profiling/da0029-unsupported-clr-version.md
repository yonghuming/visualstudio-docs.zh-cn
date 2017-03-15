---
title: "DA0029：不支持的 CLR 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# DA0029：不支持的 CLR 版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0029|  
|类别|分析工具使用|  
|分析方法|通过命令行进行分析|  
|消息|收集期间检测到了不支持的 CLR 版本。  托管符号可能解析不正确。|  
|规则类型|信息。|  
  
## 原因  
 您尝试分析的应用程序使用不受分析工具支持的 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]。  
  
## 规则说明  
 由于分析工具无法解析该应用程序中运行的托管代码的符号，因此，将出现此警告。  分析工具无法解析运行 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)]的应用程序的托管代码符号。  
  
## 如何解决冲突  
 无。