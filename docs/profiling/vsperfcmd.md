---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令行, 工具"
  - "命令行工具, VSPerfCmd 工具"
  - "性能工具, VSPerfCmd 工具"
  - "分析工具, VSPerfCmd"
  - "VSPerfCmd 工具"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 49
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**VSPerfCmd.exe** 工具用于启动和停止性能数据收集。  它使用以下语法：  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 下表介绍 **VSPerfCmd.exe** 工具选项：  
  
|选项|说明|  
|--------|--------|  
|**U**|重定向控制台的输出编写为 Unicode。  必须是指定的第一个选项。|  
|[Start](../profiling/start.md) **:** `mode`|在指定模式下启动分析服务。|  
|[输出](../profiling/output.md) **:** `filename`|指定输出文件名。  仅与 **Start** 一起使用。|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|启用跨 Windows 会话的分析。  仅与 **Start**、 **Attach**、 **or Launch** 一起使用。|  
|[用户](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|使指定的帐户可以访问探查器服务。  仅与 **Start** 一起使用。|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|等待数据收集记录器初始化。  如果指定了 `n`，则 **VSPerfCmd** 将最多等待 `n` 秒。  如果没有指定 `n`，则 **VSPerfCmd** 将无限期等待。  这就可以很容易地将 **VSPerfCmd** 用在批处理中。|  
|[计数器](../profiling/counter.md) **:** `cfg`|使用采样分析方法时，指定 CPU 计数器和要用作采样间隔的事件数。  可以只对一个计数器值进行采样。<br /><br /> 使用检测分析方法时，指定要在每个检测点收集的 CPU 计数器。  仅与 **Start:**`Trace`、 **Attach** 或 **Launch** 一起使用。|  
|[QueryCounters](../profiling/querycounters.md)|显示当前计算机的有效 CPU 计数器列表。|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|指定要包含分析标记数据的 Windows 性能计数器事件。  仅与 **Start** 一起使用。|  
|[AutoMark](../profiling/automark.md) **:** *n*|指定两个 Windows 性能计数器数据收集事件之间的时间间隔（单位为毫秒）。  与 **WinCounter** 一起使用。|  
|[事件](../profiling/events-vsperfcmd.md) **:** `option`|控制指定的 Windows 事件跟踪 \(ETW\) 事件的收集。  ETW 数据收集到不属于分析数据 \(.vsp\) 文件的 .itl 文件中。|  
|[Status](../profiling/status.md)|显示探查器的状态、有关当前正在分析的进程的信息以及有权控制探查器的帐户。|  
|[Shutdown](../profiling/shutdown.md)\[**:**`n`\]|关闭分析数据文件并关闭探查器。|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|调用 **VSPerfCmd GlobalOff** 后恢复数据收集。|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|停止所有数据收集，但不结束分析会话。|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|在通过调用 **VSPerfCmd ProcessOff** 暂停分析后恢复指定进程的数据收集。|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|停止指定进程的数据收集。|  
|[ThreadOn 和 ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|在通过调用 **VSPerfCmd ThreadOff** 暂停分析后恢复指定进程的分析。  仅当使用检测方法进行分析时才使用 **ThreadOn**。|  
|[ThreadOn 和 ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|暂停指定线程的分析。  仅当使用检测方法进行分析时才使用 **ThreadOff**。|  
|[标记](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|将标记插入到分析数据文件中，并可根据需要插入附加文本。|  
  
## 采样方法选项  
 仅当使用采样分析方法时，下列选项才可用。  
  
|选项|说明|  
|--------|--------|  
|[Launch](../profiling/launch.md) **:** *Executable*|启动指定的应用程序并开始分析。|  
|[Args](../profiling/args.md) **:** *Arguments*|指定要传递给启动的应用程序的命令行参数。|  
|[控制台](../profiling/console.md)|在一个新的命令提示窗口中启动指定的命令。|  
|[Attach](../profiling/attach.md) **:** *PID*\[**,***PID*\]|开始分析指定的进程。  进程可由进程 ID 或进程名称来标识。|  
|[Detach](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|停止分析指定的进程。  进程可由进程 ID 或进程名称来标识。  如果未指定进程，则会中止所有进程的分析。|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|收集 .NET 内存分配和对象生存期数据。  仅与 **VSPerfCmd Launch** 选项一起使用。|  
  
### 采样间隔选项  
 下列选项指定采样间隔的类型和持续时间。  默认值为 **Timer**。  通过使用 **Counter** 选项，还可以将 CPU 计数器指定为间隔。  这些选项只能与 **Launch** 或者分析会话的第一个 **Attach** 一起指定。  
  
|选项|说明|  
|--------|--------|  
|[PF](../profiling/pf.md)\[**:***n*\]|对每 n 个页面错误取样（默认值 \= 10）。|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|对每 n 个系统调用取样（默认值 \= 10）。|  
|[Timer](../profiling/timer.md)\[**:***n*\]|在每个第 n 个处理器周期采样（默认值 \= 10000000）。|  
  
## 服务组件和内核模式设备选项  
 以下 Admin 选项支持分析服务组件或内核模式设备驱动程序。  Admin 选项设置分析权限并控制分析的服务或设备驱动程序。  
  
 必须在以管理凭据运行的命令提示下执行 Admin 选项。  
  
|选项|说明|  
|--------|--------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|允许或拒绝指定用户或组访问分析服务。<br /><br /> `Right` 可以是：<br /><br /> CrossSession – 授予用户访问服务以进行跨会话分析的权限。<br /><br /> SampleProfiling \- 授予用户访问驱动程序以启动取样分析的权限。  也用于在跟踪分析期间访问内核转换信息。<br /><br /> FullAccess \- 授予用户 CrossSession 和 SampleProfiling 访问权。|  
|**Admin:Security, List**|列出分析服务的当前状态并列出用户权限。|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|启动、停止、安装或卸载分析服务组件（服务）或内核模式设备驱动程序（驱动程序）。|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|启用或禁用重新启动后自动启动分析组件（服务）或内核模式设备驱动程序（驱动程序）。|  
  
## VSPerfCmd \/Driver  
 **VSPerfCmd \/Driver** 选项现在已过时。  请使用 **VsPerfCmd Admin** 选项来实现此功能。  
  
## 请参阅  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)