---
title: "项目的 Visual Basic 调试配置的设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc51c3d6525bcbecb0b0ef132aaa029ec7a9fcd
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2017
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Project Settings for a Visual Basic Debug Configuration
你可以更改的项目设置[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]中的调试配置**属性页**窗口，如下所述[调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)。 下表显示在何处可以找到中与调试器相关的设置**属性页**窗口。  
  
> [!WARNING]
>  本主题不适用于 UWP 应用。 请参阅[启动调试会话 (VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>“调试”选项卡  
  
|设置|描述|  
|-------------|-----------------|  
|**配置**|设置编译应用程序的模式。 选择**活动 （调试）**，**调试**，**版本**，**所有配置**。|  
|**启动操作**|这组控件指定在从“调试”菜单中选择“启动”时将发生的操作。<br /><br /> -   **启动项目**是默认值，用于启动启动项目以供调试。 有关详细信息，请参阅[NIB 如何： 设置启动项目](http://msdn.microsoft.com/en-us/31465836-0911-48db-a5d9-e456b635e970)。<br />-   **启动外部程序**使您能够启动和附加到不是程序的一部分[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目。 有关详细信息，请参阅[附加到运行进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。<br />-   **启动浏览器于 URL**使您能够调试 Web 应用程序。|  
|**命令行参数**|指定要调试的程序的命令行自变量。 该命令名是在“启动外部程序”中指定的程序名。 如果“启动操作”设置为“启动 URL”，则忽略命令行自变量。|  
|**工作目录**|指定被调试的程序的工作目录。 在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，工作目录就是启动应用程序所在的目录。 默认工作目录是 \bin\Debug 或 \bin\Release，具体取决于当前配置。|  
|**使用远程计算机**|选中此复选框后，将启用远程调试。 在文本框中，你可以键入出于调试目的运行该应用程序的远程计算机的名称或[Msvsmon 服务器名称](../debugger/remote-debugging.md)。 该 EXE 在远程计算机上的位置是由“生成”选项卡中的“输出路径”属性指定的。此位置必须是远程计算机上的共享目录。|  
|**非托管的代码调试**|使你能够从托管应用程序中调试对本机（非托管）Win32 代码的调用。 这与在 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 项目中为“调试器类型”选择“混合”的效果相同。|  
|**SQL Server 调试**|允许对 SQL Server 数据库对象进行调试。|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>编译选项卡：按“高级编译选项”按钮  
  
|设置|描述|  
|-------------|-----------------|  
|**启用优化**|此选项不应选中。 优化会导致实际执行的代码与在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中看到的源代码不一样，从而造成调试困难。 如果代码被优化，则在使用“仅我的代码”调试时，默认情况下不加载符号。|  
|**生成调试信息**|默认情况下，调试版本和发布版本中定义了此设置，它（与 /debug 编译器选项等效）在生成时创建调试信息。 在调试时，调试器使用该信息以有用的格式显示变量名和其他信息。 如果编译程序时没有该信息，则调试器的功能将受到限制。 有关详细信息，请参阅[/调试](/dotnet/visual-basic/reference/command-line-compiler/debug)。|  
|**定义 DEBUG 常数**|定义此符号将启用的输出函数的条件编译[Debug 类](/dotnet/api/system.diagnostics.debug)。 定义该符号后，Debug 类方法生成输出复制到[输出窗口](../ide/reference/output-window.md)。 如果没有该符号，则 Debug 类方法将不会被编译，并且不生成任何输出。 该符号应在调试版本中定义而不应在发布版本中定义。 在发布版本中定义该符号将创建不必要的代码，从而降低程序的速度。|  
|**定义 TRACE 常数**|定义此符号将启用的输出函数的条件编译[Trace 类](/dotnet/api/system.diagnostics.trace.aspx)。 定义了该符号，Trace 类方法将生成输出到[输出窗口](../ide/reference/output-window.md)。 如果没有该符号，则 Trace 类方法将不会被编译，并且不生成任何 Trace 输出。 默认情况下，在调试版本和发布版本中都定义了此符号。|  
  
## <a name="see-also"></a>另请参阅  
 [调试器设置和准备](../debugger/debugger-settings-and-preparation.md)