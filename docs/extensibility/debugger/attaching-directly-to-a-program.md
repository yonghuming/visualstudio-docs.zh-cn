---
title: "将直接连接到某个程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "附加到程序的调试引擎"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 将直接连接到某个程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

请需的用户调试在通常已运行的处理程序遵循此过程:  
  
1.  在 IDE 中，从 **工具** 菜单中选择 **调试进程** 命令。  
  
     即会出现**“进程”**对话框。  
  
2.  选择进程并单击 **附加** 按钮。  
  
     **附加的进程** 出现对话框，列出所有调试在计算机上安装的引擎 \(DEs\)。  
  
3.  指定 DES 使用调试选定的进程，然后单击 **好**。  
  
 调试包开始调试会话并通过 DES 列表给它。  调试会话依次通过该回调函数的列表，因此，对于选定的进程，然后处理请求枚举其运行的程序。  
  
 编程方式，以响应用户请求，调试包将实例化会话调试管理器 \(SDM\)和在选定的 DES 列表给它。  与列表时，调试包通过 SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 接口。  调试包通过 DES 列表为所选通过调用 [IDebugProcess2:: 附加](../../extensibility/debugger/reference/idebugprocess2-attach.md)处理。  SDM 然后对端口的 [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 枚举运行进程的过程。  
  
 从\+这时\+起，每个调试引擎正确地附加到程序进行了详细介绍 [将生成之后](../../extensibility/debugger/attaching-after-a-launch.md)，有两个异常。  
  
 为提高效率，分组 DES，以便每个 DE 已实现的 SDM 共享地址空间的设置程序将附加。  在这种情况下， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 调用 [IDebugEngine2:: 附加](../../extensibility/debugger/reference/idebugengine2-attach.md) 并将其附加程序。  
  
 第二个异常是 DE 发送的启动事件附加到已经运行的程序通常不包括入口点事件。  
  
## 请参阅  
 [发送应用程序启动后启动事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [调试任务](../../extensibility/debugger/debugging-tasks.md)