---
title: "Start | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Start
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Start** 选项是将探查器初始化为指定分析方法的 VSPerfCmd.exe 选项。  
  
## 语法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### 参数  
 `Method`  
 必须为下列关键字之一：  
  
-   **TRACE** \- 指定检测方法。  
  
-   **SAMPLE** \- 指定采样方法。  
  
-   **COVERAGE** \- 指定代码覆盖率。  
  
-   **CONCURRENCY** \- 指定资源争用方法。  
  
## 必需选项  
 在命令行上指定 **Start** 时，必须指定 **Output** 选项。  
  
 **Output:** `filename`  
 指定输出文件名。  
  
## 专有选项  
 以下选项只能在命令行上与 **Start** 选项一起使用。  
  
 **CrossSession**&#124;**CS**  
 启用跨进程分析。  支持选项名称 **CrossSession** 和 **CS**。  
  
 **User:**\[`domain\`\]`username`  
 使客户端可以从指定帐户访问监视器。  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** 指定要作为标记包含在分析数据文件中的 Windows 性能计数器。  **AutoMark** 指定数据文件收集之间的间隔（以毫秒为单位）。  
  
## 无效选项  
 以下选项不能在命令行上与 **Start** 选项一起使用。  
  
 **Status**  
 **Status** 应用于所分析的进程。  它列出进程和线程，以及它们当前的分析状态（开启\/关闭）。  例如，如果进程被停止，则 **Status** 将不会在报告中指示这一点。  **Status** 将显示进程已被分析还是没有被分析。  
  
 **Shutdown**\[**:**`Timeout`\]  
 关闭探查器。  
  
## 示例  
 下面的示例演示如何使用 VSPerfCmd.exe **Start** 选项初始化探查器。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)