---
title: "Status | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Status
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Status** 选项显示有关探查器状态以及当前正在分析的任何进程的信息。  
  
 **Status** 选项必须是命令行中指定的唯一选项。  必须先使用 VSPerfCmd.exe **Start** 选项初始化探查器，然后才能显示任何状态。  
  
## 语法  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### 参数  
 无  
  
## 备注  
 **Status** 选项显示探查器的以下状态信息。  
  
 **Output File Name**  
 当前探查器数据文件的路径和文件名。  
  
 **Collection Mode**  
 采样或跟踪  
  
 **Maximum Processes**  
 一次可分析的最大进程数和当前活动的进程数。  
  
 **Maximum Threads**  
 一次可分析的最大线程数。  
  
 **Number of Buffers**  
 专用于写入分析数据的内存缓冲区数。  
  
 **Size of Buffers**  
 内存缓冲区的大小（以字节为单位）。  
  
 **Status** 选项显示当前正在分析的每个进程的以下状态信息。  
  
 **Process**  
 分析的进程的名称。  
  
 **Process ID**  
 进程的系统标识符。  
  
 **Num Threads**  
 当前正在执行的线程数。  
  
 **Start\/Stop Count**  
 用于控制此进程的数据收集的主内部探查器计数。  该计数必须等于一才能收集数据。  Start\/Stop 计数可以通过探查器 API 以及 VSPerfCmd 选项 **GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff**、**ThreadOn** 和 **ThreadOff** 进行控制。  
  
 **Suspend\/Resume Count**  
 用于控制此进程的数据收集的辅助内部探查器计数。  该计数必须小于或等于零才能收集数据。  **Suspend\/Resume** 计数只能通过探查器 API 进行控制。  
  
 **Users with access rights to monitor**  
 列出有权访问探查器的用户名。  可以使用 VSPerfCmd.exe **Admin** 选项向其他用户授予访问权  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)