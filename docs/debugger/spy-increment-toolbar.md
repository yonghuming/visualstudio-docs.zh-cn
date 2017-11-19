---
title: "Spy + + 工具栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db8a6cd6832b2fa427cea539bc03add5d330e06e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="spy-toolbar"></a>Spy++ 工具栏
该工具栏显示在 Spy + + 中的菜单栏下。 若要显示或隐藏工具栏上，在**视图**菜单上，单击**工具栏**。  
  
 以下控件是在工具栏上可用。  
  
## <a name="uielement-list"></a>UIElement 列表  
  
|Button|效果|  
|------------|------------|  
|![Spy &#43; &#43;Windows 按钮](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + windows （_w)")|在系统中显示窗口和控件的树的视图。 有关详细信息，请参阅[Windows 视图](../debugger/windows-view.md)。|  
|![Spy &#43; &#43;处理按钮](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|显示系统中的进程的树视图。 有关详细信息，请参阅[进程视图](../debugger/processes-view.md)。|  
|![Spy &#43; &#43;线程按钮](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|显示系统中的线程的树视图。 有关详细信息，请参阅[线程视图](../debugger/threads-view.md)。|  
|![Spy &#43; &#43;消息按钮](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|创建在窗口中显示窗口消息并打开**消息选项**对话框中，以便你可以选择的窗口的消息将显示，并且还选择其他选项。 有关详细信息，请参阅[消息视图](../debugger/messages-view.md)。|  
|![Spy &#43; &#43;启动日志按钮](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|启动消息日志记录并显示消息流。 此控件的本质时才可用**消息**窗口是活动窗口。 有关详细信息，请参阅[如何： 启动和停止显示消息日志](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![Spy &#43; &#43;停止日志按钮](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|停止消息日志记录和显示的消息流。 此控件的本质时才可用**消息**窗口是活动窗口。 有关详细信息，请参阅[如何： 启动和停止显示消息日志](../debugger/how-to-start-and-stop-the-message-log-display.md)。|  
|![Spy &#43; &#43;日志选项按钮](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|显示[消息选项](../debugger/message-options-dialog-box.md)对话框。 使用此对话框中选择 windows 和消息类型以供查看。 此控件的本质时才可用**消息**窗口是活动窗口。|  
|![Spy &#43; &#43;清除日志按钮](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|清除的活动内容**消息**窗口。 此控件的本质时才可用**消息**窗口是活动窗口。|  
|![Spy &#43; &#43;查找窗口按钮](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|打开[查找窗口](../debugger/find-window-dialog-box.md)对话框中，您可以设置窗口搜索条件并显示属性或消息。 有关详细信息，请参阅[如何： 使用查找程序工具](../debugger/how-to-use-the-finder-tool.md)。|  
|![Spy &#43; &#43;查找第一个窗口按钮](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|当前视图匹配的窗口、 进程、 线程或消息中搜索。|  
|![Spy &#43; &#43;查找下一步窗口按钮](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|搜索下一个匹配的窗口、 进程、 线程或消息的当前视图。 仅当不是唯一有效的搜索结果时，此控件 （及相关的菜单命令） 才可用。 例如，当作为窗口树中的搜索条件中使用的窗口句柄，它会生成唯一的结果是因为只有一个窗口中的窗口树中具有该句柄;在此情况下，**查找下一个**不可用。|  
|![Spy &#43; &#43;查找上一个窗口按钮](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|搜索上一个匹配的窗口、 进程、 线程或消息的当前视图。 仅当不是唯一有效的搜索结果时，此控件 （及相关的菜单命令） 才可用。 例如，当作为窗口树中的搜索条件中使用的窗口句柄，它会生成唯一的结果是因为只有一个窗口中的窗口树中具有该句柄;在此情况下，**查找上一个**不可用。|  
|![Spy &#43; &#43;属性资源管理器按钮](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|显示在窗口视图中选择的窗口的属性。|  
|![Spy &#43; &#43;刷新按钮](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|刷新系统视图。|  
  
## <a name="see-also"></a>另请参阅  
 [使用 Spy + +](../debugger/using-spy-increment.md)   
 [Spy + + 视图](../debugger/spy-increment-views.md)   
 [Spy++ 参考](../debugger/spy-increment-reference.md)