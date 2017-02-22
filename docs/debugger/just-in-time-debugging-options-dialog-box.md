---
title: "“选项”对话框 -&gt;“调试”-&gt;“实时” | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Debugger.JIT"
  - "vs.debug.options.JIT"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "实时调试，设置选项"
  - "“选项”对话框，调试"
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “选项”对话框 -&gt;“调试”-&gt;“实时”
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要访问**“实时”**页，请转到**“工具”**菜单，然后单击**“选项”**。  在**“选项”**对话框中，展开**“调试”**节点并选择**“实时”**。  使用该页，您可以为托管代码、本机代码和脚本启用实时调试。  有关更多信息，请参见[实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)。  
  
 可以为以下程序类型启用实时调试：  
  
-   Managed  
  
-   Native  
  
-   Script  
  
 实时调试是一种用于调试在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的外部启动的程序的方法。  可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境之外运行在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建的程序。  如果已启用实时调试，则发生崩溃时会显示一个对话框，询问您是否需要调试。  
  
## 关联警告  
 访问**“选项”**对话框的此页时，可以看到类似于下面的警告消息：  
  
 **另一个调试器已将自己注册为实时调试器。  要修复，请启用实时调试或运行 Visual Studio 修复。**  
  
 如果将另一个调试器（可能为较早版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器）设置为实时调试器，则会出现此消息。  
  
 可能看到的另一条消息如下：  
  
 **检测到实时调试注册错误。  要修复，请启用实时调试或运行 Visual Studio 修复。**  
  
 如果看到这些警告中的任何一个，则使用 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 进行实时调试要求具有管理员特权，直到修复该问题为止。  如果在这些条件下尝试仅作为非管理员来启用，则会看到下面的错误消息：  
  
 **拒绝访问。  让管理员启用实时调试，或修复 Visual Studio 的安装。**  
  
## 请参阅  
 [“选项”对话框 \-\>“调试”](../debugger/debugging-options-dialog-box.md)   
 [如何：指定调试器设置](../debugger/how-to-specify-debugger-settings.md)