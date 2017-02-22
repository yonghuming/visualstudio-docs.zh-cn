---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**AutoMark** 选项指定两次收集 Windows 软件性能计数器事件之间间隔的毫秒数。  Windows 性能计数器在 **WinCounter** 选项中指定。  
  
 在命令行中只能指定一个 **AutoMark** 选项。  注意，由 **AutoMark** 指定的 **WinCounter** 采样间隔独立于主采样间隔。  
  
## 语法  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### 参数  
 `Milliseconds`  
 指定两次收集 Windows 性能计数器事件之间间隔的毫秒数。  
  
## 必需选项  
 **WinCounter:** `Path`  
 指定要收集的 Windows 性能计数器。  使用检测方法时，可以指定多个 Windows 计数器。  使用采样方法时，只能指定一个软件计数器。  只能在包含 **Start** 选项的命令行上指定 **WinCounter** 选项。  
  
## 示例  
 在此示例中，为两个 Windows 性能计数器设置了 1000 毫秒的采样间隔。  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)