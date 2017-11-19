---
title: "如何： 编辑寄存器值 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89e653ac13f92566ab350fa009de809f1712ab39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-edit-a-register-value"></a>如何：编辑寄存器值
寄存器窗口是中启用了地址级调试的情况下，才可用**选项**对话框中，**调试**节点。  
  
### <a name="to-change-the-value-of-a-register"></a>更改寄存器值  
  
1.  在**注册**窗口中，使用 TAB 键或鼠标移动插入点移动到你想要更改的值。 在开始键入之前，光标必须位于要覆盖的值之前。  
  
2.  键入新值。  
  
    > [!CAUTION]
    >  更改寄存器值（特别是 EIP 和 EBP 寄存器中的值）可能会影响程序的执行。  
  
    > [!CAUTION]
    >  编辑浮点值时，由于要将小数部分从十进制转换为二进制，因此所得的结果可能存在微小误差。 甚至看起来无关紧要的编辑都能引起浮点变量中某些最不重要的数据位发生变化。  
  
## <a name="see-also"></a>另请参阅  
 [如何：使用“寄存器”窗口](../debugger/how-to-use-the-registers-window.md)