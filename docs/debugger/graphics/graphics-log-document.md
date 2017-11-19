---
title: "图形日志文档 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8429e7175ca6ab9a537952fb4a605f2281da69c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="graphics-log-document"></a>图形日志文档
图形日志文档是对你的应用在图形诊断会话下运行时发生的图形事件的记录。 在记录后，你可以在 Visual Studio 图形分析器中检查日志，以诊断呈现和性能问题。  
  
 这是图形日志文档在图形分析器中的外观：  
  
 ![图形日志包含两个捕获的帧。] (media/gfx_diag_demo_graphics_log_orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>了解图形日志文档  
 通过使用图形分析器检查图形日志文档，便能可视化捕获期间在呈现器目标上发生的 Direct3D 事件的效果。 你可以查明包含意外输出的呈现器目标的区域。 选择受影响区域中的某个像素后，你可以使用图形诊断检查它、它的着色器、影响它的 Direct3D 事件、导致这些事件的应用程序调用堆栈，以及支持这些事件的 DirectX 对象。 你可以使用此信息诊断游戏或应用中的呈现问题。  
  
 窗口的顶部 (**Graphics Experiment.vsglog**) 显示所选的帧和底部显示的当前呈现器目标输出**帧列表**，其中包含的缩略图图像捕获的帧。  
  
#### <a name="to-inspect-a-frame"></a>检查帧  
  
-   在**帧列表**，选择你想要检查的帧。 更新图形日志文档顶部的呈现器目标输出以显示所选帧。  
  
#### <a name="to-inspect-a-pixel"></a>检查像素  
  
-   在图形日志文档顶部，从呈现器目标输出中选择所需像素。 选中某个像素后，你可以使用**图形像素历史记录**窗口，以查看有关所选像素的详细的信息。 有关详细信息，请参阅[像素历史记录](graphics-pixel-history.md)。  
  
## <a name="playback-machine"></a>播放计算机  
 此外显示在右上角的**帧列表**是**播放机**。 播放计算机是指用于在之后的图形诊断会话期间，播放图形日志文件中的图形事件的计算机或设备。 通过使用另一台设备而非你的开发计算机来播放捕获的事件，你可以更加准确地重现发生问题所在的执行环境，例如，你可以使用具有不同于开发计算机使用的图形硬件或驱动程序的计算机或其他种类的设备（例如基于 ARM 的 Windows RT 平板电脑或 Windows Phone 设备）。  
  
 有关如何指定播放计算机的信息，请参阅[如何： 更改图形诊断播放机](how-to-change-the-graphics-diagnostics-playback-machine.md)。  
  
## <a name="graphics-log-summary-information"></a>图形日志摘要信息  
 当图形日志文件是活动文档时，**属性**窗口显示有关托管图形诊断捕获会话的环境的信息。 将显示以下几种类别的信息。  
  
 **Direct3D 信息**  
 列出有关在捕获会话期间使用的显示适配器的硬件和驱动程序功能的信息。  
  
|属性|描述|  
|--------------|-----------------|  
|**10 位 XR 高颜色格式**|**True**如果 10 位 XR 高颜色格式，则受支持; 否则为**False**。|  
|**DirectCompute CS 4.x**|**True**计算着色器 4.0，则受支持; 否则为如果**False**。|  
|**双精度着色器**|**True**如果显示适配器支持双精度 （64 位） 浮点值; 否则为**False**。|  
|**驱动程序命令列表**|**True**如果驱动程序支持命令列表; 否则为**False**。|  
|**驱动程序并发创建**|**True**如果驱动程序支持并发 （异步） 创建; 否则为**False**。|  
|**扩展的格式 （BGRA 等）**|**True** BGRA 等其他的格式是否受支持; 否则为**False**。|  
|**最大硬件功能级别**|显示显示适配器所支持的最高功能级别。|  
  
 **显示信息**  
 列出有关在捕获会话期间使用的显示适配器的信息。  
  
|属性|描述|  
|--------------|-----------------|  
|**描述**|显示适配器描述字符串。|  
|**显示内存**|安装在图形适配器上的内存量。|  
|**驱动程序名称**|图形适配器驱动程序的名称。|  
|**驱动程序版本**|图形适配器驱动程序的版本。|  
|**Name**|图形适配器的名称。|  
  
 **试验文件**  
 列出有关与捕获会话相关联的试验文件的信息。  
  
|属性|描述|  
|--------------|-----------------|  
|**Path**|.vsglog 文件的路径。 **注意：**下旧版捕获，此属性是未使用。|  
  
 **模块信息**  
 列出有关在捕获会话期间由应用加载的动态链接库 (DLL) 的名称和版本。  
  
 **系统信息**  
 列出有关在捕获会话期间托管应用的硬件和操作系的信息。  
  
|属性|描述|  
|--------------|-----------------|  
|**内存**|安装在计算机中的内存量。|  
|**操作系统体系结构**|操作系统的目标 CPU 体系结构。|  
|**操作系统版本**|操作系统版本。|  
|**处理器**|安装在计算机中的处理器。|  
|**目标应用程序体系结构**|应用的目标 CPU 体系结构。 这可以是不同于**操作系统体系结构**。|  
  
 **目标应用程序**  
 列出有关作为捕获期间的使用者的应用的信息。  
  
|属性|描述|  
|--------------|-----------------|  
|**上次修改日期/时间**|应用的生成日期和时间。|  
|**Path**|应用的路径。|  
|**进程 ID**|已提供给应用的进程 ID。|  
|**Version**|应用版本。|  
  
 **VSG 日志文件**  
 列出有关图形日志文档的信息。  
  
|属性|描述|  
|--------------|-----------------|  
|**创建的**|创建了图形日志文档的应用的名称。 例如，如果已从 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中初始化捕获会话（手动捕获），则此属性的值为 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。|  
|**会话开始时间**|捕获会话开始的日期和时间。|  
|**Size**|图形日志文档的大小。|  
  
## <a name="see-also"></a>另请参阅  
 [演练： 因顶点着色而缺少对象](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [演练：调试因着色引起的呈现错误](walkthrough-debugging-rendering-errors-due-to-shading.md)