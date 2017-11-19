---
title: "在调试器中创建的数据的自定义视图 |Microsoft 文档"
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dad9291e60577bd5d6faec557931ac3dcd37c45a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>在 Visual Studio 调试器中创建数据的自定义的视图
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器提供了各种用于检查和修改程序状态的工具。 这些工具中的大多数仅在中断模式下有效。

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>在变量窗口和数据提示中创建数据的自定义的视图
 许多[调试器窗口](../debugger/debugger-windows.md)，如**自动**和**监视**windows，允许你在调试时检查变量。 你可以自定义显示本机类型和托管的对象在调试器变量窗口和[数据提示](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)。 这可以帮助以显示在自己的应用程序中创建的类型。 有关详细信息，请参阅[创建本机对象的自定义视图](../debugger/create-custom-views-of-native-objects.md)和[创建托管对象的自定义视图](../debugger/create-custom-views-of-dot-managed-objects.md)。
  
## <a name="create-custom-visualizers"></a>创建自定义可视化工具  
 可视化工具，可以查看对象或变量的内容中有意义的方式。 在 Visual Studio 调试器中，可视化工具是指使用的放大镜图标可以打开不同 windows ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "可视化工具图标")。 例如，可以使用 HTML 可视化工具来查看 HTML 字符串，因为这样可以解释该字符串并在浏览器中显示出来。 你可以通过数据提示、 **“监视”** 窗口、 **“自动”** 窗口、 **“局部变量”** 窗口或 **“快速监视”** 对话框来访问可视化工具。 有关详细信息，请参阅[创建自定义可视化工具](../debugger/create-custom-visualizers-of-data.md)。
  
## <a name="see-also"></a>另请参阅  
 [Debugger Basics](../debugger/debugger-basics.md) （调试器基础知识）  
 [“命令”窗口](../ide/reference/command-window.md)   
 [调试器安全](../debugger/debugger-security.md)