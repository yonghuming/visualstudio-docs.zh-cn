---
title: "如何： 调用工作流调试器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: "9"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d7fbdb1851669d704cb8a44f8144291c04ae0ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-invoke-the-workflow-debugger"></a>如何：调用工作流调试器
通常，您可以像调试用其他 Visual Studio 编程语言编写的程序那样调试工作流。 可通过以下方法启动工作流调试器：  
  
-   选择**附加到进程**上**调试**菜单选择正在运行的工作流实例的主机进程。 此过程与附加到以托管代码编写的托管进程的过程相同。  
  
-   按**F5**来启动运行实例的工作流，或继续运行后命中断点。  
  
-   使用远程调试。 有关使用远程调试的信息，请参阅[如何： 启用远程调试](http://go.microsoft.com/fwlink/?LinkId=196257)。  
  
    > [!NOTE]
    >  如果工作流应用程序针对 x86 体系结构并位于运行 64 位操作系统的计算机上远程调试将不工作，除非[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]工作流应用程序更改为安装在远程计算机或目标**任何 CPU**。  
  
### <a name="stepping-through-code"></a>逐句通过代码  
  
-   **单步执行**： 可以单步执行活动使用**F11**。 此调试器可以单步执行任何定义的处理程序。 如果未定义处理程序，则可以逐过程执行该活动，或者对于包含其他活动的复合活动，您可以单步执行第一个要执行的活动。  
  
-   **跳出：**跳出活动使用**shift-f11**。 如果跳出某个活动，则会运行当前活动及其所有同级活动，直到这些活动完成为止。 然后调试器将在当前活动的父项处中断。 从代码处理程序中跳出时，调试器将在与此处理程序关联的活动处中断。  
  
-   **逐过程**： 你可以逐过程执行活动使用**F10**。 逐过程执行复合活动时，调试器将在此复合活动的第一个可执行的子活动处中断。 逐过程执行非复合活动（例如 <xref:System.Activities.Statements.Assign> 活动）时，调试器将执行此活动及其关联的处理程序并在下一个活动处中断。 如果执行的活动是复合活动中的最后一个子活动，则在执行之后，调试器将在父活动处中断。  
  
### <a name="debugging-with-f5"></a>用 F5 调试  
  
-   如果你要生成工作流控制台应用程序项目，只需按**F5**开始调试应用程序和工作流。 如果要生成活动库自身，您必须有可执行的主机应用程序作为启动项目。 在中设置启动项目**解决方案资源管理器**，右键单击项目名称的主机，然后选择**设为启动项目**。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 在工作流中设置断点](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [使用工作流设计器调试工作流](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)