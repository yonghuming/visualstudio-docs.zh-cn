---
title: "图形事件调用堆栈 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81a7edd908da5953e04e68a1a903ed585f1ec6b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="graphics-event-call-stack"></a>图形事件调用堆栈
Visual Studio 图形分析器中的图形事件调用堆栈可帮助你映射有问题的图形事件和应用的源代码之间的关系。  
  
 这就是“事件调用堆栈”窗口：  
  
 ![调用堆栈 DrawIndexed 事件。] (media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>了解图形事件调用堆栈  
 你可以使用“事件调用堆栈”来了解导致特定 Direct3D 事件的执行流。 此过程类似于 Visual Studio 调用堆栈窗口中，只不过而不是在正在运行的应用中显示当前线程的当前调用堆栈，则显示调用堆栈如其存在所选的 Direct3D 事件发生时。 你可以从“事件调用堆栈”跳转到选定的 Direct3D 事件的调用站点，以检查周围的代码。  
  
 通过使用“事件调用堆栈”标识问题事件源自的代码路径，你可以使用你的代码库知识推导出问题可能的来源，或者可以在应用源代码中添加断点，以便使用传统调试技术检查应用或事件参数的状态是如何导致事件错误行为的。 这一检查可以帮助你在源代码中找到问题，这些问题只显示为呈现问题。  
  
### <a name="graphics-event-call-stack-information"></a>图形事件调用堆栈信息  
 调用堆栈不支持预框架事件或用户定义的事件。 图形事件的调用堆栈以表格形式显示。  
  
|列|说明|  
|------------|-----------------|  
|**Name**|包含调用站点的函数的唯一标识符号。 这个函数的调试符号在它可用时显示；否则将显示函数偏移量。|  
|**文件**|包含调用站点的源代码文件或库文件的文件名。|  
|**位置**|调用站点行号。|  
  
### <a name="links-to-graphics-objects"></a>指向图形对象的链接  
 若要了解选定的图形事件，你可能需要了解与它关联的 Direct3D 对象的有关信息。 **图形事件调用堆栈**窗口提供此信息的链接。  
  
## <a name="see-also"></a>另请参阅  
 [演练：因顶点着色而缺少对象](walkthrough-missing-objects-due-to-vertex-shading.md)