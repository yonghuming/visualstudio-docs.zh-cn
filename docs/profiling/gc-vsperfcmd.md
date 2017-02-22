---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**GC** 选项启用 .NET Framework 内存分配数据和对象生存期数据的收集。  **GC** 选项只能用于采样分析方法，且只能与 **Launch** 选项一起使用。  
  
 使用 **GC** 选项时，不需要 VSPerfClrEnv **\/sampleon** 命令。  
  
 如果未指定任何参数，或者如果指定了 **Allocation** 参数，则只会收集 .NET Framework 内存分配数据。  如果指定了 **Lifetime** 参数，则会同时收集 .NET Framework 内存分配数据和 .NET Framework 对象生存期数据。  
  
## 语法  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### 参数  
 **Allocation**  
 默认值。  收集 .NET Framework 内存分配数据。  
  
 **Lifetime**  
 同时收集 .NET Framework 内存分配数据和 .NET Framework 对象生存期数据。  
  
## 必需选项  
 **GC** 选项只能与 **Launch** 选项一起使用。  
  
 **Launch:** `AppName`  
 启动指定的应用程序并用采样方法开始分析。  
  
## 示例  
 以下示例启动一个应用程序，并收集 .NET Framework 内存分配数据。  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)