---
title: "JIT 优化和调试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "调试 [Visual Studio], 优化的代码"
  - "优化的代码, 调试"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# JIT 优化和调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当调试托管应用程序时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会默认取消优化实时 \(JIT\) 代码。  取消 JIT 优化意味着您调试的是非优化代码。  由于代码未优化，因此代码会运行得稍慢一些，但您的调试体验会更全面。  由于调试优化代码要更难一些，因此建议仅在遇到优化代码中发生的 bug 无法在非优化版本中重现时使用。  
  
 JIT 优化在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中由**“在模块加载时取消 JIT 优化”**选项控制。  您可以在**“选项”**对话框中**“调试”**节点下的**“常规”**页上找到此选项。  
  
 如果清除**“在模块加载时取消 JIT 优化”**选项，您可以调试优化 JIT 代码，但调试的能力会由于优化代码与源代码不匹配而可能受到限制。  因此，调试器窗口（如**“局部变量”**和**“自动”**窗口）显示的信息可能没有调试非优化代码时显示的信息那么多。  
  
 另一个重要差异是有关使用“仅我的代码”进行调试。  如果您正在使用“仅我的代码”进行调试，调试器就会将优化代码作为非用户代码处理，不在调试时显示。  因此，在调试 JIT 优化代码时，您可能想关闭“仅我的代码”。  有关详细信息，请参阅[限制单步执行“仅我的代码”](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)。  
  
 切记，当模块加载时，**“在模块加载时取消 JIT 优化”**选项会取消代码优化。  如果附加到已正在运行的进程，它可能包含已加载的代码、JIT 编译的代码和优化的代码。  **“在模块加载时取消 JIT 优化”**选项对这些代码无效，尽管它会影响在附加后加载的模块。  此外，**“在模块加载时取消 JIT 优化”**选项不影响用 NGEN 创建的模块，如 WinForms.dll。  
  
## 请参阅  
 [调试托管代码](../debugger/debugging-managed-code.md)   
 [使用调试器浏览代码](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加到运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [托管执行过程](../Topic/Managed%20Execution%20Process.md)