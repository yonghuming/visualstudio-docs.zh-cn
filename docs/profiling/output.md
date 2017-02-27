---
title: "输出 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 输出
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Output** 选项指定性能会话的分析数据文件文件的名称。  **Output** 选项必须与 **Start** 选项一起使用。  
  
## 语法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### 参数  
 `FileName`  
 数据文件的名称。  接受完整路径和部分路径。  如果未指定路径，则将在当前目录中创建该文件。  
  
## 必需选项  
 **Output** 选项必须与 **Start** 选项一起使用。  
  
 **Start:** `Method`  
 指定输出文件名。  
  
## 示例  
 下面的示例中，在当前目录中创建分析数据文件。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## 请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)