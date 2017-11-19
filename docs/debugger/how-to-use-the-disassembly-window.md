---
title: "在 Visual Studio 中的调试器中查看反汇编代码 |Microsoft 文档"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c72de947262cd87e4920d87c2d4d54664e02cc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>在 Visual Studio 调试器中查看反汇编代码
仅当启用了地址级调试后提供了此功能**选项**对话框中，**调试**节点。 但对于脚本或 SQL 调试是不可用的。  
  
 **反汇编**窗口显示与编译器所创建的指令对应的汇编代码。 如果正在调试托管代码，则这些汇编指令对应于由实时 (JIT) 编译器创建的本机代码，而不是由 Visual Studio 编译器生成的 Microsoft 中间语言 (MSIL)。  
  
 程序集指令，除了**反汇编**窗口可以显示如下可选信息：  
  
-   每条指令所在的内存地址 对于本机应用程序，这是实际内存地址。 对于 Visual Basic、C# 或托管代码，这是距离函数开头的偏移量。  
  
-   程序集代码派生于的源代码。  
  
-   代码字节 — 实际计算机或 MSIL 指令的字节表示形式。  
  
-   内存地址的符号名。  
  
-   对应于源代码的行号。  
  
 汇编语言指令由助记符（指令名称的缩写）和代表变量、寄存器以及常量的符号所组成。 每一条机器语言指令由一个汇编语言助记符代表，通常其后还跟有一个或多个变量、寄存器或常量。  
  
 如果您无法阅读汇编语言但又想充分利用“反汇编”窗口，请参考有关汇编语言编程的好书。 汇编语言编程超出了我们对“反汇编”窗口进行简单介绍的讨论范围。  
  
 汇编语言代码在很大程度上依赖处理器的寄存器（对托管代码而言，依赖公共语言运行时寄存器），您将发现协同使用“反汇编”窗口和“寄存器”窗口将很有用，可以允许您检查寄存器内容。  
  
 您很可能愿意使用汇编语言，而从来不会愿意或需要查看原始的、数字形式的机器代码指令。 不过，如果愿意的话，可以利用“内存”窗口或从“反汇编”窗口的快捷菜单中选取“代码字节”来查看。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-display-the-disassembly-window"></a>显示“反汇编”窗口  
  
-   在调试过程选择**调试 > Windows** ，然后单击**反汇编**。
  
### <a name="to-turn-optional-information-on-or-off"></a>打开或关闭可选信息  
  
-   右键单击**反汇编**窗口中，并设置或清除快捷菜单中所需的选项。  
  
     左边距中的黄色箭头表示当前执行点的位置。 对于本机代码，这对应于 CPU 的程序计数器。 该位置显示程序中将要执行的下一条指令。  
  
     有关详细信息，请参阅[分页向上或在内存中的向下](../debugger/how-to-page-up-or-down-in-memory.md)。  
  
## <a name="see-also"></a>另请参阅  
 [在调试器中查看数据](../debugger/viewing-data-in-the-debugger.md)   
 [如何：使用“寄存器”窗口](../debugger/how-to-use-the-registers-window.md)