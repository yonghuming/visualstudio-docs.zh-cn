---
title: "如何： 调试插入的代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76656372df3282efb3ec6354391517a248ffcf7b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-injected-code"></a>如何：调试插入的代码
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在“工具”菜单上选择“导入和导出设置”。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
 使用特性可大大简化 C++ 编程。 有关详细信息，请参阅[概念](/cpp/windows/attributed-programming-concepts)。 某些特性由编译器直接解释。 其他特性则向程序源中插入代码，然后由编译器进行编译。 此类插入的代码通过减少您必须编写的代码量使编程变得更容易。 但有时 bug 可能导致应用程序在执行插入的代码时失败。 发生这种情况时，您可能希望查看插入的代码。 Visual Studio 提供两种查看插入的代码的方法：  
  
-   你可以查看插入的代码中**反汇编**窗口。  
  
-   使用[/Fx](/cpp/build/reference/fx-merge-injected-code)，你可以创建合并的源文件，其中包含原始代码和插入代码。  
  
 **反汇编**窗口显示与源代码和特性所插入代码对应的汇编语言指令。 此外，**反汇编**窗口可以显示源代码批注。  
  
### <a name="to-turn-on-source-annotation"></a>打开源批注  
  
-   右键单击**反汇编**窗口中，选择**显示源代码**从快捷菜单。  
  
     如果知道特性在源窗口中的位置，你可以使用快捷菜单查找插入的代码中**反汇编**窗口。  
  
### <a name="to-view-injected-code"></a>查看插入的代码  
  
1.  调试器必须处于中断模式。  
  
2.  在源代码窗口中，将光标放在要查看其插入代码的特性前面。  
  
3.  右键单击，然后选择**转到反汇编**从快捷菜单。  
  
     如果特性位置在当前执行点附近，你可以选择**反汇编**从窗口**调试**菜单。  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>查看当前执行点处的反汇编代码  
  
1.  调试器必须处于中断模式。  
  
2.  从**调试**菜单上，选择**Windows**，然后单击**反汇编**。  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试本机代码](../debugger/debugging-native-code.md)