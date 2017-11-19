---
title: "在本地计算机上运行 UWP 应用 |Microsoft 文档"
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
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e0108a3fb7a93dc19fe1aa96988912068ace70
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>本地计算机上运行的 UWP 应用
![仅适用于 Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 若要调试、 测试或在 UWP 应用上运行性能分析，你可以运行应用程序在同一计算机上承载 Visual Studio。 如果设备上的显示屏支持触控，你可以执行应用的完整功能；否则，你只能使用有限的鼠标和键盘手势。  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>如何在本地计算机上运行  
 若要在本地计算机上运行应用程序，选择**本地计算机**调试器上的启动调试按钮旁的下拉列表中**标准**工具栏。  
  
 ![本地计算机上运行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 如果看不到**标准**工具栏上，单击**视图**菜单上，指向**工具栏**，然后单击**标准**。  
  
 你在下拉列表中所做的选择将保留在项目属性文件中，并成为默认的运行目标。  
  
 你也可以直接在项目属性文件中设置运行目标。 右键单击中的项目名称**解决方案资源管理器**，然后选择**属性**。 然后，执行下列操作之一：  
  
-   在 C# 和 Visual Basic 项目中，单击**调试**，然后选择**本地计算机**从**目标设备**下拉列表。  
  
     ![使用 c&#35;和 Visual Basic 项目属性页](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   在 c + + 和 JavaScript 项目中，展开**配置属性**节点，单击**调试**，然后选择**本地调试器**从**调试器若要启动**列表。  
  
     ![C# 43; &#43;和 JavaScript 项目属性页](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  