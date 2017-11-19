---
title: "调试 DLL 项目 |Microsoft 文档"
ms.custom: 
ms.date: 05/23/2017
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
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92d888c04827f3df2c9bc5ede33d4dfd9a6742dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>从 Visual Studio 的调试 DLL 项目
下面的 Visual Studio 模板创建 Dll:  
  
-   （C++、C# 和 Visual Basic）：类库   

-   （c + +）： Win32 控制台 DLL 项目
  
     有关更多信息，请参见 [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md)。

-   （C++、C# 和 Visual Basic）：Windows 窗体控件库
  
     调试 Windows 窗体控件库是类似于调试类库项目。 大多数情况下将从另一个项目中调用 Windows 控件。 调试调用项目时，可单步执行 Windows 控件的代码，并设置断点，然后执行其他调试操作。 有关详细信息，请参阅 [Windows 窗体控件](/dotnet/framework/winforms/controls/index)。  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 无论如何启动调试，都请首先确保生成 DLL 的调试版本，并确保该调试版本位于应用程序应该能够找到它的位置。 这似乎很明显，但如果忘记这一步骤，应用程序可能会找到并加载 DLL 的其他版本。 然后程序将继续运行，尽管您会奇怪为什么断点从未被命中。 调试时，可以通过打开调试器的 **“模块”** 窗口来检查程序已加载的 DLL。 **“模块”** 窗口列出了所调试进程中加载的每个 DLL 或 EXE。 有关详细信息，请参阅 [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md)。  
 为了使调试器附加到用 C++ 编写的代码，该代码必须发出 `DebuggableAttribute`。 可通过链接 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 链接器选项将它自动添加到代码中。  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 调用 DLL 的调用应用程序可以用托管代码编写，也可以用本机代码编写。 如果托管 DLL 由本机代码调用，并且您需要调试两者，则必须同时启用托管调试器和本机调试器。 你可以选择在**\<项目 > 属性页**对话框或窗口。 具体如何检查取决于是从 DLL 项目中启动调试，还是从调用应用程序项目中启动调试。 有关更多信息，请参见 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)。  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 用项目模板创建控制台应用程序项目时， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将自动为调试和发布配置创建所需的设置。 必要时，可更改这些设置。 有关详细信息，请参阅[用于 c + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)， [C# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)， [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，和[如何： 设置调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 本节的每个项目都创建一个 DLL。 您无法直接运行 DLL，它必须由应用程序（通常为 EXE）调用。 有关详细信息，请参阅 [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects)。 调用应用程序可能满足下列任一条件：  
  
-   内置在同一 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 解决方案中包含类库的另一个项目中的应用程序。  
  
-   已经部署到测试或生产计算机上的现有应用程序。  
  
-   位于 Web 上并通过 URL 访问。  
  
-   包含嵌入了 DLL 的网页的 Web 应用程序。  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
若要调试 DLL，请从调试调用应用程序开始，通常是 EXE 或者 Web 应用程序。 调试方式有许多种。  
  
-   如果有调用应用程序的项目，则可以打开该项目并从 **“调试”** 菜单开始执行。 有关详细信息，请参阅[调试器入门](../debugger/getting-started-with-the-debugger.md)。  
  
-   如果调用应用程序是已经部署到测试或生产计算机上并已经运行的现有程序，则可以附加到该应用程序上。 如果 DLL 是由 Internet Explorer 承载的控件或网页上的控件，请使用此方法。 有关详细信息，请参阅 [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
-   您可以从 DLL 项目中调试。 有关详细信息，请参阅 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)。  
  
-   您可以从中进行调试[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][即时窗口](#vxtskdebuggingdllprojectstheimmediatewindow)。 在这种情况下， **“即时”** 窗口充当应用程序的角色。  
  
在开始调试调用应用程序之前，通常希望在类库中设置一个断点。 有关详细信息，请参阅 [Using Breakpoints](../debugger/using-breakpoints.md)。 命中断点时，可以逐句通过代码，同时观察每行的操作，直到将问题隔离出来。 有关详细信息，请参阅[浏览在调试器中的代码](../debugger/navigating-through-code-with-the-debugger.md)。
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> “即时”窗口  
 可以在没有调用应用程序的情况下计算 DLL 中的函数或方法。 可以进行设计时调试并使用 **“即时”** 窗口。 若要以这种方式进行调试，请在 DLL 项目打开时按照以下步骤操作：  
  
1.  打开调试器 **“即时”** 窗口。  
  
2.  若要测试类 `Test` 中名为 `Class1`的方法，请通过在“即时”窗口中键入以下 C# 代码来实例化类型为 `Class1` 的对象。 对语法进行以下适当更改后，此托管代码对 Visual Basic 和 C++ 有效：  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     在 C# 中，所有名称必须是全限定名称。 而且，任何方法或变量都必须处在调试会话的当前范围和上下文中。  
  
3.  假设 `Test` 带有一个 `int` 参数，使用 `Test` “即时” **窗口计算** ：  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     结果将打印在 **“即时”** 窗口中。  
  
4.  您可以继续调试 `Test` ，方法为在其中设置断点然后再次计算函数：  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     断点将被命中，然后您将可以逐步调试 `Test`。 当执行离开 `Test`后，调试器将返回设计模式。

## <a name="vxtskdebuggingdllprojectsexternal"></a>调试 c + + 项目的外部 DLL

如果你正在调试的 DLL 外部到你的项目，可用 （如逐句通过代码） 的调试功能将依赖于[的 DLL 的调试配置](#vxtskdebuggingdllprojectsbuildingadebugversion)已生成时，以及是否[.pdb 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)且可提供其他所需的 dll 文件。

你的项目需要要能够查找 DLL 和用于调试的.pdb 文件。 你可以创建自定义生成任务以将复制到这些文件**\<项目文件夹 > \Debug**输出文件夹，也可以将文件复制到输出文件夹中手动。

可以轻松地在属性页中设置的标头文件和 *.lib 文件的位置 (右键单击 c + + 项目并选择**查看属性**，然后选择**所有配置**) 而无需复制它们到输出文件夹：

- C/c + + 文件夹 （常规类别）-指定包含中的标头文件的文件夹**附加包含目录**字段。
- 链接器文件夹 （常规类别）-指定包含中的.lib 文件的文件夹**附加库目录**字段。 
- 链接器文件夹 （输入类别）-指定的完整路径和文件名中的.lib 文件**附加依赖项**字段。

时的配置是否正确，你可以通过开始从执行来调试**调试**菜单。

项目设置的详细信息，请参阅[属性页 （Visual c + +）](/cpp/ide/property-pages-visual-cpp)。
  
## <a name="see-also"></a>另请参阅  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [Visual c + + 项目类型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F#、和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [对于 C# 的项目设置调试配置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [调试配置适用于 Visual Basic 项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [调试器安全](../debugger/debugger-security.md)