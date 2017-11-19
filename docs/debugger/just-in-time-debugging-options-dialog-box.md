---
title: "在实时，调试，选项对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4648ecb0ce1b62256cdf2fe297c0d8cb4ccb17e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="just-in-time-debugging-options-dialog-box"></a>“选项”对话框 ->“调试”->“实时”
访问**中实时**页上，转到**工具**菜单，然后单击**选项**。 在**选项**对话框框中，展开**调试**节点，然后选择**中实时**。 使用该页，你可以为托管代码、本机代码和脚本启用实时调试。 有关详细信息，请参阅[实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)。  
  
 可以为以下程序类型启用实时调试：  
  
-   Managed  
  
-   Native  
  
-   脚本  
  
 实时调试是一种用于调试在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的外部启动的程序的方法。 可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境之外运行在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中创建的程序。 如果已启用实时调试，则发生崩溃时会显示一个对话框，询问您是否需要调试。  
  
## <a name="associated-warnings"></a>关联警告  
 当你访问的此页**选项**对话框中，你可能会看到一条警告消息如下：  
  
 **另一个调试器已将自己注册为实时调试器。若要修复，启用的实时调试或运行 Visual Studio 修复。**  
  
 如果将另一个调试器（可能为较早版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器）设置为实时调试器，则会出现此消息。  
  
 可能看到的另一条消息如下：  
  
 **在实时检测到调试注册错误。若要修复，启用的实时调试或运行 Visual Studio 修复。**  
  
 如果你看到这些警告，任一实时调试与[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]在解决此问题之前，需要管理员特权。 如果在这些条件下尝试仅作为非管理员来启用，则会看到下面的错误消息：  
  
 **访问被拒绝。具有管理员启用中实时调试，或修复 Visual Studio 的安装。**  
  
## <a name="see-also"></a>另请参阅  
 [调试，选项对话框](../debugger/debugging-options-dialog-box.md)   
 [如何：指定调试器设置](../debugger/how-to-specify-debugger-settings.md)