---
title: "如何： 调用堆栈窗口中的缺少本机框架时跳出托管代码 |Microsoft 文档"
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
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38fa4b37b008aca07b26b859f50767344dcafd9c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>如何：在“调用堆栈”窗口中缺少本机框架时跳出托管代码
如果代码中有中不可见的本机框架**调用堆栈**窗口中，托管代码中跳出会产生意外的结果。 作为一种解决方法，你可以使用断点来代替**单步跳出**。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>要在本机框架从调用堆栈显示中消失时跳出托管代码  
  
1.  在本机代码中，调用托管代码的后面设置一个位置断点。  
  
2.  上**调试**菜单上，选择**继续**。  
  
     托管调用完成后，执行会在本机代码的断点处停止。  
  
## <a name="see-also"></a>另请参阅  
 [如何：使用“调用堆栈”窗口](../debugger/how-to-use-the-call-stack-window.md)