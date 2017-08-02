---
title: "Spy++ Toolbar | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Spy\+\+ 中工具栏显示在菜单栏下方。  要显示或隐藏“工具栏”，请在“视图”菜单中单击“工具栏”。  
  
 工具栏中的以下控件可用。  
  
## UIElement 列表  
  
|Button|效果|  
|------------|--------|  
|![“Spy&#43;&#43; 窗口”按钮](~/debugger/media/icon_spy--_windows.gif "Icon\_Spy\+\+\_Windows")|在系统中显示窗口和控件的树视图。  有关更多信息，请参见 [Windows View](../debugger/windows-view.md)。|  
|![“Spy&#43;&#43; 进程”按钮](~/debugger/media/icon_spy--_processes.gif "Icon\_Spy\+\+\_Processes")|在系统中显示进程的树视图。  有关更多信息，请参见 [Processes View](../debugger/processes-view.md)。|  
|![“Spy&#43;&#43; 线程”按钮](~/debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|在系统中显示线程的树视图。  有关更多信息，请参见 [Threads View](../debugger/threads-view.md)。|  
|![“Spy&#43;&#43; 消息”按钮](~/debugger/media/icon_spy--_messages.gif "Icon\_Spy\+\+\_Messages")|创建用来显示消息的窗口并且打开**“消息选项”**对话框，以便您可以选择显示消息的窗口以及其他选项。  有关更多信息，请参见 [Messages View](../debugger/messages-view.md)。|  
|![“Spy&#43;&#43; 启动日志”按钮](~/debugger/media/icon_spy--_startlog.gif "Icon\_Spy\+\+\_StartLog")|开始记录消息并显示消息流。  仅当“消息”窗口处于活动状态时，此控件才可用。  有关更多信息，请参见 [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![“Spy&#43;&#43; 停止日志”按钮](~/debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|停止记录消息和显示消息流。  仅当“消息”窗口处于活动状态时，此控件才可用。  有关更多信息，请参见 [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![“Spy&#43;&#43; 日志选项”按钮](~/debugger/media/icon_spy--_logoptions.gif "Icon\_Spy\+\+\_LogOptions")|显示 [“绘图选项”](../debugger/message-options-dialog-box.md) 对话框。  使用此对话框可选择要查看的窗口和消息类型。  仅当“消息”窗口处于活动状态时，此控件才可用。|  
|![Spy&#43;&#43;“清除日志”按钮](~/debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|清除活动**“消息”**窗口的内容。  仅当“消息”窗口处于活动状态时，此控件才可用。|  
|![“Spy&#43;&#43; 查找窗口”按钮](~/debugger/media/icon_spy--_findwindow.gif "Icon\_Spy\+\+\_FindWindow")|打开允许您设置窗口搜索条件以及显示属性或消息的[查找窗口](../debugger/find-window-dialog-box.md)对话框。  有关更多信息，请参见 [How to: Use the Finder Tool](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md)。|  
|![“Spy&#43;&#43; 查找第一个窗口”按钮](~/debugger/media/icon_spy--_window.gif "Icon\_Spy\+\+\_Window")|在当前视图中搜索匹配的窗口、进程、线程或消息。|  
|![“Spy&#43;&#43; 查找下一个窗口”按钮](~/debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|在当前视图中搜索下一个匹配的窗口、进程、线程或消息。  仅当有效搜索结果不唯一时，此控件（及相关菜单命令）才可用。  例如，如果您使用窗口句柄作为窗口树中的搜索条件，将生成唯一的结果，这是因为窗口树中只有一个窗口具有该句柄；在这个实例中，**“查找下一个”** 不可用。|  
|![“Spy&#43;&#43; 查找上一个窗口”按钮](~/debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|在当前视图中搜索上一个匹配的窗口、进程、线程或消息。  仅当有效搜索结果不唯一时，此控件（及相关菜单命令）才可用。  例如，如果您使用窗口句柄作为窗口树中的搜索条件，将生成唯一的结果，这是因为窗口树中只有一个窗口具有该句柄；在这个实例中 **“查找下一个”** 不可用。|  
|![“Spy&#43;&#43; 属性资源管理器”按钮](~/debugger/media/icon_spy--_propexp.gif "Icon\_Spy\+\+\_PropExp")|显示在窗口视图中选择的窗口的属性。|  
|![“Spy&#43;&#43; 刷新”按钮](~/debugger/media/icon_spy--_refresh.gif "Icon\_Spy\+\+\_Refresh")|刷新系统视图。|  
  
## 请参阅  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)