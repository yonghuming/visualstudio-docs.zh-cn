---
title: "GPU 活动关系图 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 964846b5a2cc06eaf03fa695e4f1c0aeb9efdca4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-graph"></a>GPU 活动关系图
并发可视化工具中的 GPU 活动图显示系统上的 DirectX 活动级别，此活动级别通过一段时间内使用的 DirectX 引擎数来衡量。  此图不显示使用了哪些特定引擎。  如果引擎正在处理任意 GPU 工作，则将视为正在使用此引擎。  
  
## <a name="gpu-activity-graph-colors"></a>GPU 活动图颜色  
 绿色表示当前进程使用的 DirectX 引擎数。  
  
 浅灰色表示系统上其他进程使用的 DirectX 引擎数。 若要减少其他进程使用的 DirectX 引擎数，请减少系统上运行的其他进程数。  
  
 白色表示系统上未使用的 DirectX 引擎的可用性。 如果可以找到更多利用机会，这些引擎就可以用于您的进程。 一些引擎只能用于特定种类的任务。  
  
## <a name="see-also"></a>另请参阅  
 [使用率视图](../profiling/utilization-view.md)