---
title: "JIT 优化和调试 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acf75c0fbf6f5c3cfcf645d288c4e5e2eb2450d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="jit-optimization-and-debugging"></a>JIT 优化和调试
当调试托管应用程序，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]会默认取消优化实时 (JIT) 代码。 取消 JIT 优化意味着你调试的是非优化代码。 由于代码未优化，因此代码会运行得稍慢一些，但您的调试体验会更全面。 由于调试优化代码要更难一些，因此建议仅在遇到优化代码中发生的 bug 无法在非优化版本中重现时使用。  
  
 在中控制 JIT 优化[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]通过**在模块加载时取消 JIT 优化**选项。 您可以在找到此选项**常规**下页上**调试**中的节点**选项**对话框。  
  
 如果你清除**在模块加载时取消 JIT 优化**选项，则可以调试优化的 JIT 代码，但调试的能力可能是有限，因为优化的代码与源代码不匹配。 因此，如调试器窗口**局部变量**和**自动**窗口可能不会显示调试非优化代码会尽可能多的信息。  
  
 另一个重要差异是有关使用“仅我的代码”进行调试。 如果您正在使用“仅我的代码”进行调试，调试器就会将优化代码作为非用户代码处理，不在调试时显示。 因此，在调试 JIT 优化代码时，你可能想关闭“仅我的代码”。 有关详细信息，请参阅[限制单步执行仅我的代码](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)。  
  
 请记住，**在模块加载时取消 JIT 优化**选项会取消代码优化，当模块加载时。 如果附加到已正在运行的进程，它可能包含已加载的代码、JIT 编译的代码和优化的代码。 **在模块加载时取消 JIT 优化**选项不起对这些代码，尽管它会影响在附加后加载的模块。 此外，**在模块加载时取消 JIT 优化**选项不影响用 NGEN 创建的模块，如 WinForms.dll。  
  
## <a name="see-also"></a>另请参阅  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [Navigating through Code with the Debugger](../debugger/navigating-through-code-with-the-debugger.md) （使用调试器浏览代码）  
 [将附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [托管执行过程](/dotnet/standard/managed-execution-process)