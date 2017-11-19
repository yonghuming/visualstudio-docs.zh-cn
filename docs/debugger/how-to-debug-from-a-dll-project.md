---
title: "如何： 从 DLL 项目调试 |Microsoft 文档"
ms.custom: 
ms.date: 05/24/2017
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
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 371c48282b2f775833287046ed9810f0cbc8f69e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>如何： 从 DLL 项目在 Visual Studio 中调试
调试 DLL 项目的一种方法是在 DLL 项目的项目属性中指定调用应用程序，然后你可以开始调试从 DLL 项目本身。 要使用此方法，应用程序必须调用该 DLL，并且该 DLL 必须在应用程序能够找到它的位置 （否则为应用程序可能找到 DLL 的不同版本并将其加载相反，且它不会命中断点）。 调试 Dll 的其他方法，请参阅[调试 DLL 项目](../debugger/debugging-dll-projects.md)。
  
如果本机代码调用了托管 DLL，而你想对这两者进行调试，则可以在项目属性中指定此项。 有关更多信息，请参见 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)。   

C++ 属性页的布局和内容与 C# 和 Visual Basic 属性页的不同。 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>在 C++ 项目中指定调用应用程序  
  
1.  右键单击中的项目节点**解决方案资源管理器**和选择**属性**。  
  
2.  请确保**配置**窗口顶部的字段设置为**调试**。 

    A**调试**配置，才能使用此方法。 
  
3.  转到**配置属性 > 调试**。  
  
4.  在**要启动的调试器**列表中，选择**本地 Windows 调试器**或**远程 Windows 调试器**。  
  
5.  在**命令**或**远程命令**框中，添加调用应用程序 （例如.exe 文件） 的完全限定路径名称。

    ![调试属性窗口](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  添加到任何必要的程序参数**命令参数**框。  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>在 C# 或 Visual Basic 项目中指定调用应用程序  
  
1.  右键单击中的项目节点**解决方案资源管理器**和选择**属性**，然后选择**调试**选项卡。

2.  请确保**配置**窗口顶部的字段设置为**调试**。

3.  (.NET framework)选择**启动外部程序**，并添加调用应用程序的完全限定路径名称。

4.  （.NET 核心）选择**可执行文件**从**启动**列表，并将调用应用程序中的完全限定路径名称**可执行文件**字段。 
  
     如果你需要添加外部程序的命令行参数，则添加它们**命令行自变量**(或**应用程序自变量**) 字段。

    ![调试属性窗口](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  如果需要你还可以调用一个应用程序作为 URL。 (如果你正在调试由本地 ASP.NET 应用程序使用的托管 DLL，则可能想要执行此操作。)  
  
     下**启动操作**，选择**使用 URL 启动浏览器：**单选按钮，并填写 URL。
  
### <a name="to-start-debugging-from-the-dll-project"></a>从 DLL 项目启动调试  
  
1.  在 DLL 项目中设置断点。 

2.  右键单击 DLL 项目并选择**设为启动项目**。 

    (此外，请确保**解决方案配置**字段仍设置为**调试**。)   
  
3.  开始调试 (按 F5，单击绿色箭头，或单击**调试 > 启动调试**)。

    在您的 DLL 中，将命中断点。 如果你不能够命中断点，请确保您的 DLL 输出 (默认情况下， **project\Debug**文件夹) 处于位置调用应用程序应该能够找到它。
  
## <a name="see-also"></a>另请参阅  
 [调试 DLL 项目](../debugger/debugging-dll-projects.md)   
 [对于 C# 的项目设置调试配置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [调试配置适用于 Visual Basic 项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)