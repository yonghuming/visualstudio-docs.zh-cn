---
title: "如何：调试 OnStart 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OnStart 方法"
  - "调试 [Visual Studio], Windows 服务"
  - "调试托管代码, OnStart 方法"
  - "调试 Windows 服务应用程序, OnStart 方法"
  - "Windows 服务应用程序, 调试"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：调试 OnStart 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过启动 Windows 服务并将调试器附加到服务进程，可以调试 Windows 服务。 有关详细信息，请参阅[如何：调试 Windows 服务应用程序](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md)。 但是，若要调试 Windows 服务的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> 方法，必须从该方法内部启动调试器。  
  
1.  将对 <xref:System.Diagnostics.Debugger.Launch%2A> 的调用添加到 `OnStart()` 方法的开头。  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  启动服务（可以使用 `net start`，或在“服务”窗口中启动）。  
  
     将显示一个对话框，如下所示：  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  选择“是，调试 \<服务名\>。”  
  
4.  在“实时调试器”窗口中，选择你想要用于调试的 Visual Studio 版本。  
  
     ![JustInTimeDebugger](~/docs/debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  将启动 Visual Studio 新实例，并在 `Debugger.Launch()` 方法处停止执行。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试托管代码](../debugger/debugging-managed-code.md)