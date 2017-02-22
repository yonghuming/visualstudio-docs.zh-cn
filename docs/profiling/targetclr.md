---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**TargetCLR** 选项指定在应用程序加载了多个版本的公共语言运行时 \(CLR\) 时，要分析的 CLR 的版本。  
  
 默认情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具以应用程序加载的第一个 CLR 版本为目标。  
  
## 语法  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### 参数  
 `ClrVersion`  
 CLR 的版本号。  使用版本格式 **vN.N.NNNNN**。  
  
## 必需选项  
 **TargetCLR** 选项只能与 **Launch** 或 **Attach** 选项一起使用。  
  
 **Launch:** `AppName`  
 启动指定的应用程序并开始分析。  
  
 **Attach:** `PID`  
 开始分析指定的进程。  
  
## 示例  
 在此示例中，使用 TargetCLR 选项以确保分析 CLR 版本 4.0.11003。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```