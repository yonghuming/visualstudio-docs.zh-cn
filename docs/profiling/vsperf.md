---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 **VsPerf** 命令行工具：  
  
1.  当 Visual Studio 在设备时，不安装配置文件中存储从命令行运行的应用。  
  
2.  使用采样分析方法分析 Windows 桌面8 应用程序和 Windows Server 2012 应用程序。  
  
 有关 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) 命令行选项的更多信息，请参见 。  
  
##  <a name="BKMK_In_this_topic"></a> 主题内容  
 本主题描述可使用 `vsperf.exe` 命令行工具的选项。  本主题包含以下各节：  
  
 [只有Windows 应用商店应用](#BKMK_windows_store_apps_only)  
  
 [仅Windows 8桌面应用程序和 Windows Server 2012 应用程序](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [所有应用程序。](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> 只有Windows 应用商店应用  
 这些选项仅适用于中存储应用。  
  
|||  
|-|-|  
|**\/app:{AppName}**|启动探查器并等待指定的应用从"开始"菜单启动。<br /><br /> 运行 `vsperf /listapps` 查看安装的应用应用名称和 PackageFullName。|  
|**\/package:{PackageFullName}**|启动探查器并等待指定的应用从"开始"菜单启动。<br /><br /> 运行 `vsperf /listapps` 查看安装的应用应用名称和 PackageFullName。|  
|**\/js**|分析 JavaScript 应用。<br /><br /> 从 JavaScript 应用收集性能数据。<br /><br /> 只能用 \/package 或 \/attach。|  
|**\/noclr**|可选。   不收集CLR数据。<br /><br /> 只能用 \/package 或 \/attach。<br /><br /> 优化，将不解析任何托管符号。|  
|**\/listapps**|列出已安装的应用名称和 PackageFullNames。|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> 仅Windows 8桌面应用程序和 Windows Server 2012 应用程序  
 这些选项在中存储应用不起作用。  
  
|||  
|-|-|  
|**\/launch:{Executable}**|开始和开始配置文件指定的可执行文件。|  
|**\/args:{ExecutableArguments}**|指定命令行参数传递 **\/launch** 目标。|  
|**\/console**|在新的命令窗口的 **\/launch** 目标。|  
  
##  <a name="BKMK_All_applications"></a> 所有应用程序。  
 这些选项适用于所有 Windows 8 或 Windows Server 2012 应用程序。  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|从指定的进程收集数据。<br /><br /> 使用任务管理器查看进程 ID \(PID\) 并处理连续应用名称。|  
|**\/file:{ReportName}**|可选。  指定输出文件名 \(覆盖现有文件\)。<br /><br /> 只能用 \/package 或 \/attach。|  
|**\/pause**|暂停数据收集。|  
|**\/resume**|继续数据收集。|  
|**\/stop**|停止数据收集并停止目标进程。|  
|**\/detach**|停止数据收集，但允许目标进程继续运行。|  
|**\/status**|探查器显示状态。|  
  
## 请参阅  
 [分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)