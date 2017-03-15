---
title: "User (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# User (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**User** 选项指定拥有所分析进程的帐户的域和用户名。  仅当运行进程的用户不是已登录用户时，才需要此选项。  进程所有者列在 Windows 任务管理器的“进程”选项卡上的“用户名”列中。  
  
 只能在同时包含 **Start** 选项的命令行上指定 **User** 选项。  
  
## 语法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### 参数  
 `Domain`  
 用户的域的名称。  
  
 `UserName`  
 用户的名称。  
  
## 必需选项  
 **User** 选项只能与 **Start** 选项一起使用。  
  
 **Start:** `Method`  
 将探查器初始化为指定的分析方法。  
  
## 示例  
 下面的示例演示如何使用 **User** 选项。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)