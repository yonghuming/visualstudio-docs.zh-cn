---
title: Start | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7da3855a699ae350c24646386d3b1a7e39520b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="start"></a>Start
**Start** 选项是一个 VSPerfCmd.exe 选项卡，可将探查器初始化为指定分析方法。  
  
## <a name="syntax"></a>语法  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>参数  
 `Method`  
 必须是以下关键字之一：  
  
-   **TRACE** - 指定检测方法。  
  
-   **SAMPLE** - 指定采样方法。  
  
-   **COVERAGE** - 指定代码覆盖率。  
  
-   **CONCURRENCY** - 指定资源争用方法。  
  
## <a name="required-options"></a>必需选项  
 在命令行上指定 **Start** 时，必须指定 **Output** 选项。  
  
 **Output:** `filename`  
 指定输出文件名。  
  
## <a name="exclusive-options"></a>独占选项  
 以下选项只能在命令行上与 **Start** 选项一起使用。  
  
 **CrossSession**&#124;**CS**  
 启用跨进程分析。 同时支持选项名 **CrossSession** 和 **CS**。  
  
 **User:**[`domain\`]`username`  
 使客户端可以用指定帐户访问监视器。  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** 指定要作为标记包含在分析数据文件中的 Windows 性能计数器。 **AutoMark** 以毫秒为单位指定数据文件的收集之间的间隔。  
  
## <a name="invalid-options"></a>无效选项  
 以下选项不能在命令行上与 **Start** 选项一起使用。  
  
 **Status**  
 **Status** 应用于进行分析的进程。 它列出进程和线程及其当前分析状态 (On/Off)。 例如，如果某个进程已停止，则 **Status** 不会在报告中对此进行指示。 **Status** 会显示该进程是否进行分析。  
  
 **Shutdown**[**:**`Timeout`]  
 关闭探查器。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 VSPerfCmd.exe **Start** 选项来初始化探查器。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [分析独立应用程序](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [分析 ASP.NET Web 应用程序](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [分析服务](../profiling/command-line-profiling-of-services.md)