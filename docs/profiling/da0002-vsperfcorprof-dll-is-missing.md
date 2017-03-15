---
title: "DA0002：缺少 VSPerfCorProf.dll | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002：缺少 VSPerfCorProf.dll
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0002|  
|类别|分析工具使用|  
|分析方法|使用 VSPerfCmd 和 VSPerfASPNETCmd 命令行工具分析|  
|消息|它将显示在未正确设置环境变量的情况下以 VSPerfCLREnv.cmd 收集文件。  托管二进制文件的符号可能未解析。|  
|规则类型|信息|  
  
## 原因  
 探查器未能在分析运行期间找到 VSPerfCorProf.dll。  当使用命令行工具收集探查器数据，但未使用 VSPerfCLREnv.cmd 工具初始化必要的环境变量时，将出现此警告。  如果分析工具启动时运行的是另一个探查器，也可能会激发警告。  
  
## 规则说明  
 分析运行前必须设置特定的环境变量，探查器才能解析.NET Framework 二进制文件中的符号。  此警告表示，收集分析数据前不会运行 VSPerfCLREnv.cmd 工具。  托管二进制文件的符号可能未解析。  有关使用命令行分析工具的更多信息，请参见[通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## 如何解决冲突  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具中使用命令行工具分析托管应用程序时，先运行 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 命令行工具，然后再开始收集数据。