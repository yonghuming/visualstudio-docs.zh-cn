---
title: "使用旧版状态机工作流设计器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "EventDrivenActivity 活动"
  - "SetStateActivity 活动"
  - "状态机工作流设计器"
  - "状态机工作流, 活动"
  - "状态机工作流, 设计器"
  - "StateActivity 活动"
  - "StateFinalizationActivity 活动"
  - "StateInitializationActivity 活动"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 使用旧版状态机工作流设计器
在 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 中创建面向 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 或 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] 的新状态机工作流项目时，可选择使用**状态机工作流控制台应用程序**或**状态机工作流库**旧项目模板。如果选择其中一个状态机项目模板，则会以旧工作流设计器用户界面的形式呈现状态机设计器。有关旧状态机项目模板的信息，请参见[如何：创建状态机工作流控制台应用程序（旧版）](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)和[如何：创建一个状态机工作流库（旧版）](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)。  
  
 状态机工作流由一组状态组成。一个状态被指示为初始状态。每个状态都可以接收一组特定事件。视事件而定，可以转换到另一个状态。状态机工作流可以有最终状态。当转换到最终状态时，工作流将完成。  
  
## 状态机设计器视图  
 状态机设计器是一种自由形式的设计器，这意味着可以在设计图面上自由移动活动。状态机设计器有两个视图：“状态”视图和“事件驱动”视图。  
  
 状态视图显示状态活动和可包含在状态活动内的事件驱动的活动。在此视图中，从一个状态到另一个状态的转换是由直线表示的，这些直线从一个状态中的事件驱动活动延伸到另一个状态。也可以通过自己绘制直线来创建转换。若要绘制转换，请选择事件驱动的活动，然后选择活动上的某个手柄并拖动该手柄。此操作将绘制直线。此直线随后将连接到目标状态，指示状态之间的转换。  
  
 若要访问事件驱动的视图，请双击事件驱动的活动。出现的设计器与顺序工作流设计器很像。在设计器的顶部，导航栏显示直到所显示事件驱动活动为止的活动层次结构。可以通过单击显示的层次结构中的任意元素导航回状态视图。如果已在状态视图中绘制了从一个状态到另一个状态的转换，并且正在显示该活动的事件驱动视图，则会为您将一个已设置状态活动添加到事件驱动的活动。如果更改已设置状态活动的属性，它将反映到状态视图中。  
  
## 状态机工作流活动  
 下表描述了状态机工作流设计器中使用的关键活动。  
  
|工具箱名称|活动|说明|  
|-----------|--------|--------|  
|**状态**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|表示状态机中的一个状态；可能包含其他 **StateActivity** 活动。有关更多信息，请参见[使用 StateActivity 活动](http://go.microsoft.com/fwlink?LinkID=65083)（可能为英文网页）。|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|指定到新状态的转换。有关更多信息，请参见[使用 SetStateActivity 活动](http://go.microsoft.com/fwlink?LinkID=65082)（可能为英文网页）。|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|在进入某个状态时执行；可能包含其他活动。有关更多信息，请参见[使用 StateInitialization 活动](http://go.microsoft.com/fwlink?LinkID=65006)（可能为英文网页）。|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|在离开 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) 活动时执行包含的活动。有关更多信息，请参见[使用 StateFinalizationActivity 活动](http://go.microsoft.com/fwlink?LinkID=65008)（可能为英文网页）。|  
|**EventDriven**|[EventDrivenActivity（可能为英文网页）](http://go.microsoft.com/fwlink?LinkID=65029)|用于依赖于外部事件开始执行的状态。**EventDrivenActivity** 活动必须具有实现 [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) 接口作为第一个子活动的活动。有关更多信息，请参见[使用 EventDrivenActivity 活动](http://go.microsoft.com/fwlink?LinkID=65068)（可能为英文网页）。|  
  
 状态机工作流中的主要组成部分是 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) 活动。在状态机工作流中的不同位置捕获了事件时，将会进入不同的状态，以处理与这些事件关联的任务。在工作流的生存期内，工作流可能会离开和进入若干不同的状态。这些状态通过使用 [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) 活动互相连接。  
  
 将新的 **StateActivity** 拖到工作流设计图面上时，您可以添加 [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)、[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)、[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043) 或其他 **StateActivity** 活动作为子活动。  
  
> [!CAUTION]
>  使用状态机工作流设计器来创建工作流时，必须使用**“文档大纲”**视图窗口来监视所设计工作流的结构。**“文档大纲”**视图窗口中状态机工作流结构的视图反映了工作流标记文件中活动的逻辑布局。工作流活动显示在设计图面上的物理布局可能不会反映工作流标记文件中活动的逻辑布局。  
>   
>  若要打开**“文档大纲”**窗口，请在**“视图”**菜单上指向**“其他窗口”**，然后选择**“文档大纲”**。  
  
## 请参阅  
 [如何：创建状态机工作流控制台应用程序（旧版）](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)   
 [如何：创建一个状态机工作流库（旧版）](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)   
 [状态机工作流](http://go.microsoft.com/fwlink?LinkID=65016)   
 [使用 StateActivity 活动](http://go.microsoft.com/fwlink?LinkID=65083)   
 [使用 StateInitializationActivity 活动](http://go.microsoft.com/fwlink?LinkID=65006)   
 [使用 StateFinalizationActivity 活动](http://go.microsoft.com/fwlink?LinkID=65008)   
 [使用 SetStateActivity 活动](http://go.microsoft.com/fwlink?LinkID=65082)   
 [使用 EventDrivenActivity 活动](http://go.microsoft.com/fwlink?LinkID=65068)