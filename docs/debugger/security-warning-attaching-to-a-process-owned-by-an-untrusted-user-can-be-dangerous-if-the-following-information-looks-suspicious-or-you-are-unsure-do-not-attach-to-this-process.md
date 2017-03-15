---
title: "安全警告: 附加到不受信任的用户拥有的进程可能很危险。如果下面的信息看上去可疑或无法确定，请不要附加到此进程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 安全警告: 附加到不受信任的用户拥有的进程可能很危险。如果下面的信息看上去可疑或无法确定，请不要附加到此进程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果附加到包含部分可信代码或由不可信用户拥有的进程，则在该附加操作发生之前，会出现此警告对话框。  包含恶意代码的不可信进程可能会损害执行调试的计算机。  如果有理由不信任该进程，则应单击**“取消”**阻止调试。  
  
 若要禁止此警告在调试合法方案时出现，请关闭 Visual Studio，并将此注册表项的值设置为 1：`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`，然后重新启动 Visual Studio。  在调试完方案后，请将值重置为 0，并重新启动 Visual Studio。  
  
 “可信用户”包括您自己以及一组标准用户，通常在安装有 .NET Framework 的计算机上定义了这些用户（如 `aspnet`、`localsystem`、`networkservice` 和 `localservice`）。  
  
## UIElement 列表  
 名称  
 为调试而请求的程序集的名称  
  
 用户  
 当前用户  
  
 Attach  
 按下它即可通过附加来继续进行调试  
  
 不附加  
 不附加到进程  
  
## 请参阅  
 [附加到运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [调试器安全](../debugger/debugger-security.md)