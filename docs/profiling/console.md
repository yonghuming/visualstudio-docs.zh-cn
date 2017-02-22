---
title: "控制台 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 控制台
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Console** 选项在新的命令提示符窗口中启动指定的应用程序。  **Console** 选项只能与 VSPerfCmd **Launch** 选项一起使用。  如果应用程序不是命令行应用程序，则 **Console** 不起作用。  
  
## 语法  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### 参数  
 无  
  
## 必需选项  
 只能在同时包含 **Launch** 选项的命令行上指定 **Console**。  
  
 **Launch:** `AppName`  
 启动探查器以及由 `AppName` 指定的应用程序。  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)