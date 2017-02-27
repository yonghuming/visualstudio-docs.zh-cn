---
title: "针对 HPC（高性能计算）群集进行分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.hpc.wizard.exeoptions"
  - "vs.performance.hpc.wizard.summary"
  - "vs.performance.hpc.wizard.startoptions"
  - "vs.performance.hpc.wizard.intro"
  - "vs.performance.hpc.property.basic"
  - "vs.performance.hpc.wizard.application"
  - "vs.performance.hpc.wizard.clusteroptions"
  - "vs.performance.hpc.property.advanced"
helpviewer_keywords: 
  - "分析工具, HPC"
  - "HPC 分析"
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 针对 HPC（高性能计算）群集进行分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过使用 [!INCLUDE[vsPreExt](../profiling/includes/vspreext_md.md)]或 [!INCLUDE[vsUltExt](../profiling/includes/vsultext_md.md)]分析工具的采样方法，可以针对 Microsoft Windows HPC 群集的计算节点进行分析。  有关 HPC 的更多信息，请参见 Microsoft 网站上的 [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393)。  
  
## 先决条件  
 若要针对 HPC 计算节点进行分析，必须执行以下操作：  
  
-   在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]所在的计算机上安装 Microsoft HPC Pack 2008。  此计算机不必是 HPC 群集的一部分。  可以在 [Microsoft 下载中心](http://go.microsoft.com/fwlink/?LinkID=177414)安装 HPC Pack\(包\)。  
  
-   在 HPC 计算节点上安装 [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)]和独立版本的分析工具。  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 和独立探查器的安装程序，适用于 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 安装媒体。  **注意** ，在您安装 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 后，在安装分析工具之前，必须重新启动计算机。  
  
 若要在活动 HPC 计算节点上安装 [!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)]和独立版本的分析工具，并对群集计算机启用分析，请执行以下步骤：  
  
1.  打开 HPC Pack 随附的命令提示符窗口。  
  
2.  在单独的命令提示符下，键入以下命令：  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|群集头节点的名称。|  
|*%FxPath%*|[!INCLUDE[net_v40_long](../profiling/includes/net_v40_long_md.md)]安装程序的路径。  在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]安装媒体上，该路径为：WCU\\dotNetFramework\\dotNetFx40\_Full\_x86\_x64.exe|  
|*%ProfilerPath%*|独立版本的分析工具安装程序的路径。  在 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]安装媒体上，该路径为：Standalone Profiler\\x64\\vs\_profiler.exe|  
  
## 针对 HPC 计算节点进行分析  
 通过使用 HPC 性能向导指定 HPC 群集和目标信息可以配置分析会话。  可以在“性能会话”属性页中设置附加选项。  分析工具自动部署必需的目标二进制文件并启动探查器和 HPC 应用程序。  
  
#### 针对 HPC 计算节点进行分析  
  
1.  在**“分析”**菜单上，单击**“启动 HPC 性能向导”**。  如果命令不可用，请确保已安装了上面列出的系统必备组件。  
  
2.  在向导的第一页上单击**“下一步”**。  
  
3.  在向导的第二页上，选择要分析的应用程序。  
  
    -   若要分析 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中当前打开的项目，请选择**“一个或多个可用项目”**选项，然后从列表中选择项目名称。  
  
    -   若要分析打开的项目中未包含的二进制文件，请选择**“可执行文件\(.EXE 文件\)”**选项。  
  
4.  单击**“下一步”**。  
  
5.  在向导的第三页上：  
  
    -   如果所分析的可执行文件不在打开的项目中，请在**“可执行文件的完整路径是什么”**中指定二进制文件的路径。  
  
    -   如果所分析的可执行文件不在打开的项目中，您可以在**“命令行参数”**中指定要传递到进程中的任意命令行参数。  
  
    -   在**“远程工作目录”**中，指定进程实例在单个计算节点上使用的文件夹的路径。  
  
    -   在**“部署位置”**中，指定 HPC 服务器用于暂存部署图像的目录的路径。  
  
6.  单击**“下一步”**。  
  
7.  在向导的第四页上：  
  
    -   在**“头节点”**列表中，单击分析运行期间用作 HPC 头节点的计算机。  头节点可以为“localhost”，这样，您可以针对本地计算机执行分析，而无需进行群集。  
  
    -   在**“进程数”**列表中，单击要运行的应用程序的实例数。  
  
    -   从**“分析选项”**列表中，选择分析目标。  
  
         若要分析群集中的特定进程，请选择**“针对轶分析”**选项，然后从下拉列表中选择进程的级别。  
  
         若要分析 HPC 群集中特定节点上运行的一个或多个进程，请选择**“针对节点分析”**选项，然后从下拉列表中选择节点。  
  
8.  单击**“下一步”**。  
  
9. 在向导的第五页上，可以选择立即启动探查器和分析过程，或者稍后使用性能资源管理器启动分析。  
  
    -   选择**“在向导完成后启动分析”**以立即启动分析，或者清除该复选框以手动启动分析。  
  
10. 单击**“完成”**。  
  
## 使用性能会话属性页设置 HPC 分析属性  
 可以在性能会话属性页的 HPC 启动属性页上更改在 HPC 分析向导上设置的性能会话属性。  可以在“HPC 高级属性”页上设置附加选项。  
  
#### 打开性能会话属性页  
  
1.  如有必要，在性能资源管理器中打开性能会话 \(.psess\) 文件。  在**“文件”**菜单上，单击**“打开”**，并找到该文件。  
  
2.  在性能资源管理器中，右击性能会话名称，然后单击**“属性”**。  
  
3.  在“属性页”对话框中，使用以下方法之一：  
  
    -   单击**“常规”**，然后选择**“在 HPC 群集上收集”**以启用 HPC 分析，或者清除该复选框以禁用 HPC 分析。  
  
    -   单击**“HPC 启动属性”**以更改用于启动 HPC 应用程序的属性。  
  
    -   单击**“HPC 高级属性”**以设置附加选项  
  
### HPC 启动属性  
  
|Property|说明|  
|--------------|--------|  
|**头节点**|指定分析运行期间用作 HPC 头节点的计算机。|  
|**进程数**|指定要在已分析应用程序中运行的应用程序实例数。|  
|**针对轶分析**|若要分析群集中的特定进程，请选择**“针对轶分析”**选项，然后从下拉列表中选择进程的级别。|  
|**针对节点分析**|若要分析 HPC 群集中特定节点上运行的一个或多个进程，请选择**“针对节点分析”**选项，然后从下拉列表中选择节点。|  
|**远程工作目录**|指定进程实例在单个计算节点上使用的文件夹路径。|  
|**部署位置**|指定 HPC 服务器用于暂存部署图像的目录的路径。|  
  
### 高级属性  
  
|Property|说明|  
|--------------|--------|  
|**项目名称**|当前 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 项目或解决方案的名称。|  
|**探查器停止时进行清理**|如果为 true，则移除已部署到执行目录的二进制文件。  由用户程序创建的文件和目录不会在此步骤中移除。  如果执行目录和部署目录由 IDE 创建，则 IDE 将尝试移除执行目录和部署目录，但如果它们的文件未由 IDE 部署，则 IDE 不会尝试此操作。|  
|**其他要部署的文件**|指定要在计算节点上部署的任何其他文件的列表（以分号分隔）。  可单击省略号按钮 \(**...**\) 来显示一个对话框，然后通过该对话框来选择多个文件。|  
|**Mpiexec 命令**|指定用于启动 MPI 应用程序的应用程序。  默认值为 **mpiexec.exe**|  
|**Mpiexec 参数**|指定要传递给 mpiexec.exe 命令的参数。|  
|**该群集中的所请求的节点**|指定群集上要运行应用程序的节点数。|  
|**部署 CRT 文件**|如果为 true，则在群集上部署 C\/C\+\+ 运行时。|  
|**分析前脚本**|指定在开始分析会话之前要在本地开发计算机上运行的脚本的路径和文件名。|  
|**分析前脚本参数**|指定要传递给分析前脚本的参数。|  
|**分析后脚本**|指定在结束分析会话之后要在本地开发计算机上运行的脚本的路径和文件名。|  
|**分析后脚本参数**|指定要传递给分析后脚本的参数。|