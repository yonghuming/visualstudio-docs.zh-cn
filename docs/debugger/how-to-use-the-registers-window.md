---
title: "在 Visual Studio 调试器中查看寄存器值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1cff6db85b29b4db6006d37fd21e2d9b109b099e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>查看注册的值和使用 Visual Studio 调试器中的注册窗口
寄存器窗口是中启用了地址级调试的情况下，才可用**选项**对话框中，**调试**节点，**常规**类别。  
  
 **注册**窗口显示寄存器内容。 如果保留**注册**窗口中打开逐步执行程序时，你可以看到寄存器值的变化在代码执行。 最近更改过的值显示为红色。 您可以编辑寄存器的值。 有关详细信息，请参阅[如何： 编辑寄存器值](../debugger/how-to-edit-a-register-value.md)。  
  
 为了减少混乱，**注册**窗口将寄存器组织成组，具体情况随平台和处理器类型。 可以根据需要显示或隐藏组。 有关详细信息，请参阅[如何： 显示和隐藏寄存器组](../debugger/how-to-display-and-hide-register-groups.md)。  
  
 有关概念寄存器和寄存器窗口的简要介绍，请参阅[调试基础知识： 寄存器窗口](../debugger/debugging-basics-registers-window.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-display-the-registers-window"></a>显示“寄存器”窗口  
  
-   上**调试**菜单上，选择**Windows**，然后选择**注册**。  
  
     调试器必须正在运行或处于中断模式。  
  
    > [!NOTE]
    >  寄存器信息对于脚本或 SQL 应用程序不可用。  
  
## <a name="see-also"></a>另请参阅  
 [调试基础知识: 寄存器窗口](../debugger/debugging-basics-registers-window.md)   
 [在调试器中查看数据](../debugger/viewing-data-in-the-debugger.md)   
 [调试基础知识：“寄存器”窗口](../debugger/debugging-basics-registers-window.md)