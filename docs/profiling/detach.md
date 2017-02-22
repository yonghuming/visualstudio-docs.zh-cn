---
title: "Detach | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Detach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe 的 **Detach** 选项可断开探查器与指定进程或所有进程（如果未指定）的连接。  必须已使用采样方法初始化分析。  
  
 使用 **Launch** 或 **Attach** 选项启动的分析可以使用 **Detach** 断开连接。  使用后续的 **Attach** 命令可以重新附加探查器。  
  
 **Detach** 不会关闭分析数据文件。  应使用 **Shutdown** 选项结束分析并关闭数据文件。  
  
> [!NOTE]
>  如果同时指定了 **Start** 选项和 **Crosssession** 选项，则对 **VSPerfCmd \/Attach** 或 **VSPerfCmd \/Detach** 的任何调用也必须指定 **Crosssession**。  
  
## 语法  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### 参数  
 `PIDs|ProcessNames`  
 `PID` \- 一个或多个进程的数字系统标识符。  
  
 `ProcessNames` \- 进程的名称。  当命名进程有多个实例正在运行时，结果不可预知。  
  
 请用逗号分隔多个进程。  
  
 如果未指定进程，则探查器会从所有分析的进程分离。  
  
## 有效选项  
 在单个命令行上，可以将以下 **VSPerfCmd** 选项与 **Attach** 选项组合使用。  
  
 **Crosssession**  
 允许分析登录会话之外的会话中的应用程序。  如果同时指定 **Start** 选项和 **Crosssession** 选项，则为必需。  
  
## 示例  
 在以下示例中，**Detach** 命令暂停分析，**Shutdown** 命令关闭探查器数据文件。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)