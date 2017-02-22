---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **CrossSession** 选项使探查器可以从任何控制台会话收集数据。  **CrossSession** 选项必须与 **Start** 选项一起使用。  
  
 可以使用缩写形式 **CS** 代替 **CrossSession**。  
  
## 语法  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### 参数  
 无  
  
## 有效选项  
 若要在另一个会话中启用分析，必须用 **Start** 选项指定 **CrossSession** 选项。  **CrossSession** 还必须在任何后续 **VSPerfCmd Attach** 和 **Detach** 命令中指定。  
  
 **Start:** `Method`  
 **Start** 选项将探查器初始化为指定的分析方法。  
  
 **Attach:** *PID*\[**,***PID*\]  
 开始分析指定的进程。  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 停止分析指定的进程。  
  
## 示例  
 在此示例中，**CrossSession** 选项用于附加到在另一个控制台会话中启动的应用程序。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)