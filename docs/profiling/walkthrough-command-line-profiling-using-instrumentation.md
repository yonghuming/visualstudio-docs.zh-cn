---
title: "演练：使用检测进行命令行分析 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具, 演练"
  - "性能工具, 演练"
  - "性能工具, 命令行工具"
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 演练：使用检测进行命令行分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本演练指导您分析 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 独立应用程序，以通过分析工具的检测方法收集详细计时数据和调用计数数据。  在本演练中，您将完成以下任务：  
  
-   使用 [VSInstr](../profiling/vsinstr.md) 命令行工具生成检测后的二进制文件。  
  
-   使用 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 工具设置环境变量以收集 .NET 分析数据。  
  
-   使用 [VSPerfCmd](../profiling/vsperfcmd.md) 工具收集分析数据。  
  
-   使用 [VSPerfReport](../profiling/vsperfreport.md) 工具生成分析数据的基于文件的报表。  
  
## 系统必备  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   C\# 的理解程度为中等  
  
-   使用命令行工具的理解程度为中等  
  
-   [PeopleTrax 示例](../profiling/peopletrax-sample-profiling-tools.md)的副本  
  
-   若要使用分析提供的信息，最好有调试符号信息。  有关更多信息，请参见[如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)。  
  
## 使用检测方法进行命令行分析  
 检测是一种分析方法，其中分析的二进制文件的特殊生成版本在检测模块中包含在函数入口和出口收集执行时间信息的探测函数。  由于此分析方法比取样更具有侵略性，它将导致更多系统开销。  检测的二进制文件也比调试或发布的二进制文件大，它们不能用于部署。  
  
> [!NOTE]
>  不要将检测的二进制文件发送给客户。  检测的二进制文件有多种风险。  除了安全风险，二进制文件中包含的信息使您的应用程序更易于被反向工程处理。  
  
#### 通过使用检测方法分析 PeopleTrax 应用程序  
  
1.  安装 PeopleTrax 示例应用程序并生成发布版本。  
  
2.  打开命令提示符窗口，将**“分析工具”**目录添加到本地 Path 环境变量。  
  
3.  将工作目录更改为包含 PeopleTrax 二进制文件的目录。  
  
4.  创建目录以包含基于文件的报表。  键入以下命令：  
  
    ```  
    md Reports  
    ```  
  
5.  使用 VSInstr 命令行工具检测应用程序中的二进制文件。  在单独的命令行中，键入以下命令：  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **注意** 默认情况下，VSInstr 会保存原始文件的未检测备份。  该备份文件的扩展名为 .orig。  例如，“MyApp.exe”的初始版本将另存为“MyApp.exe.orig”。  
  
6.  键入以下命令以设置合适的环境变量：  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  若要启动探查器，请键入以下命令：  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  以跟踪模式启动探查器后，运行 PeopleTrax.exe 进程的已检测版本来收集数据。  
  
     将出现**“PeopleTrax”**应用程序窗口。  
  
9. 单击**“获取 People”**。  
  
     PeopleTrax 数据网格将出现数据。  
  
10. 单击**“导出数据”**。  
  
     记事本将会启动并显示一个包含来自**“PeopleTrax”**应用程序的人的列表的新文件。  
  
11. 关闭“记事本”，然后关闭**“PeopleTrax”**应用程序。  
  
12. 关闭探查器。  键入以下命令：  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. 键入以下命令以重置环境变量：  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. 使用 VSPerfReport 工具生成逗号分隔值 \(.csv\) 报表文件。  键入：  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     您可以在电子表格程序中分析已生成的报表，也可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 分析 Report.vsp 文件中的分析数据。  有关更多信息，请参见[对分析工具数据进行分析](../profiling/analyzing-performance-tools-data.md)。  
  
## 请参阅  
 [性能会话概述](../profiling/performance-session-overview.md)   
 [通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [了解采样数据值](../profiling/understanding-sampling-data-values.md)   
 [分析工具报告视图](../profiling/performance-report-views.md)