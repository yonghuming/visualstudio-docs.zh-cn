---
title: "调试接口访问 SDK | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "调试 [DIA SDK]"
  - "调试器 [DIA SDK]"
  - "DIA SDK"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试接口访问 SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Microsoft 调试接口访问软件开发工具包 \(sdk\) \(DIA SDK\) 提供对调试在程序数据库 \(.pdb\) 文件中存储的信息生成由 Microsoft postcompiler 工具。  由于 postcompiler 工具生成的 .pdb 文件的格式执行常数的版本，显示该格式不可行。  使用 DIA API，可以开发搜索浏览调试在 .pdb 文件中存储的信息的应用程序。  此类应用程序中，例如，报告堆栈跟踪信息和分析性能数据。  
  
## 本节内容  
 [入门](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 提供 DIA SDK 概述功能并指定安装 DIA SDK 以及必需的头和库文件的位置。  
  
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供有关如何使用 DIA API 查询 .pdb 文件。  
  
 [符号和符号标记](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 讨论符号和符号标记如何在 DIA API。  
  
 [参考](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 包含 DIA API 的接口、方法、枚举和结构。  
  
 [Dia2dump 示例](../../debugger/debug-interface-access/dia2dump-sample.md)  
 演示如何使用 DIA API 搜索，并浏览调试信息。  
  
 [Dia2dump.cpp 源文件](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 [Dia2dump 示例](../../debugger/debug-interface-access/dia2dump-sample.md) 使用的源代码演示 DIA API。