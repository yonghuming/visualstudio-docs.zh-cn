---
title: "在调试器中查看 Dll 和可执行文件 |Microsoft 文档"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: caaa710f0fc34a4e6a24038a7e65e5670bebd6ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>查看 Dll 和可执行文件使用 Visual Studio 调试器中的模块窗口
 
**模块**窗口列出的 Dll 与可执行文件 (EXE)，使用由你的程序并显示每个相关信息。 

> [!NOTE]
>  此功能不可用于 SQL 或脚本调试。 
  
### <a name="to-display-the-modules-window"></a>若要显示模块窗口  
  
-   在调试过程选择**调试 > Windows** ，然后单击**模块**。  
  
     默认情况下，**模块**窗口按加载顺序对模块进行排序。 但是，可以选择按任意列来排序。  
  
### <a name="to-sort-by-any-column"></a>按任意列排序  
  
-   单击该列顶部的按钮。  
  
     你可以加载符号或指定符号路径**模块**窗口是通过使用快捷菜单。  
  
## <a name="loading-symbols"></a>加载符号  
 在**模块**窗口中，你可以看到哪些模块加载了调试符号。 此信息显示在**符号状态**列。 如果该状态显示**已跳过 loadingCannot 找到或打开 PDB 文件**，或**加载包括 '/' 排除 ' 设置禁用**，则您可以指示调试器从 Microsoft 公共符号下载符号服务器或从你的计算机上的符号目录加载符号。 有关详细信息，请参阅[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>手动加载符号  
  
1.  在**模块**窗口中，右击还未加载符号的模块的。  
  
2.  指向**负载符号从**，然后单击**Microsoft 符号服务器**或**符号路径**。  
  
#### <a name="to-change-symbol-load-settings"></a>更改符号加载设置  
  
1.  在**模块**窗口中，右击任一模块。  
  
2.  单击**符号设置**。  
  
     中所述，你现在可以更改符号加载设置，[指定符号位置和加载行为](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)。 只有重新启动调试会话，更改才会生效。  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>为特定模块更改符号加载行为  
  
1.  在**模块**窗口中，右键单击该模块。  
  
2.  指向**自动符号加载设置**，然后单击**始终手动加载**或**默认**。 只有重新启动调试会话，更改才会生效。  
  
## <a name="see-also"></a>另请参阅  
 [中断执行](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [在调试器中查看数据](../debugger/viewing-data-in-the-debugger.md)   
 [指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)