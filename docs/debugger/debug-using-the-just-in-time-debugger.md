---
title: "使用实时调试器调试 |Microsoft 文档"
ms.custom: 
ms.date: 07/06/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
caps.latest.revision: "48"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 470e4c728d246570e6f7e38ff3b71772de5b05fd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>调试使用 Visual Studio 中的实时调试器
在实时调试 Visual Studio 会自动启动的应用程序正在运行 Visual Studio 外部中发生异常或崩溃时。 这使您要测试你的应用程序，如果未运行 Visual Studio，并开始使用 Visual Studio 进行调试时出现问题。

在实时调试适用于 Windows 桌面应用。 它并不适用于通用 Windows 应用，并不适合可视化工具等本机应用程序中托管的托管代码。

> [!TIP] 
> 如果你只想要知道如何响应实时调试器对话框中，请参阅[本主题](../debugger/just-in-time-debugging-in-visual-studio.md)。

##  <a name="BKMK_Enabling"></a>启用或禁用在实时调试  
你可以启用或禁用实时调试从 Visual Studio**工具 > 选项**对话框。
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>启用或禁用实时调试  
  
1.  使用管理员特权打开 Visual Studio (右键单击并选择**以管理员身份运行**)。

    启用或禁用在实时调试会设置注册表项，并可能需要管理员权限才能更改该密钥。
    
2. 在 **“工具”** 菜单上，单击 **“选项”**。
  
2.  在**选项**对话框框中，展开**调试**节点。  
  
3.  在**调试**节点中，选择**中实时**。

    ![启用或禁用 JIT 调试](../debugger/media/dbg-jit-enable-or-disable.png "启用或禁用 JIT 调试") 
  
4.  在**启用实时调试这些代码类型的**框中，选择或清除相关的程序类型：**托管**，**本机**，或**脚本**.    
  
5.  单击“确定”。  
  
即便在你的计算机中不再安装有 Visual Studio，仍可启用实时调试。 如果没有安装 Visual Studio，您不能禁用实时调试从 Visual Studio**选项**对话框。 对于这种情况，你可以通过编辑 Windows 注册表来禁用实时调试。  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>通过编辑注册表禁用实时调试  
  
1.  上**启动**菜单，搜索并运行`regedit.exe`  
  
2.  在**注册表编辑器**窗口中，找到并删除下列注册表项：  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\DbgManagedDebugger  

    ![JIT 注册表项](../debugger/media/dbg-jit-registry.png "JIT 注册表项") 
  
3.  如果你的计算机正在运行 64 位操作系统，如果还要删除下列注册表项：  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\。NETFramework\DbgManagedDebugger  
  
4.  注意不要意外删除或更改任何其他注册表项。  
  
5.  关闭**注册表编辑器**窗口。   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>为 Windows 窗体启用实时调试  
  
1.  默认情况下，Windows 窗体应用程序有一个顶级的异常处理程序，该处理程序允许程序在能够恢复时继续运行。 例如，如果你的 Windows 窗体应用程序会引发未处理的异常，你将看到一个对话框，如下所示：  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     启用在实时调试的 Windows 窗体应用程序，必须执行以下附加步骤：  
  
2.  设置`jitDebugging`值赋给`true`中`system.windows.form`一部分 machine.config 或*\<应用程序名称 >*。.exe.config 文件：  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  在 C++ Windows 窗体应用程序中，还必须在 .config 文件或你的代码中设置 `DebuggableAttribute`。 如果使用编译[/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)而[/Og](/cpp/build/reference/og-global-optimizations)，编译器会替你设置此属性。 然而，如果你想要调试非优化发布版本，则必须自行设置此项。 为此，你可以在应用程序的 AssemblyInfo.cpp 文件中添加下面一行：  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     有关更多信息，请参见<xref:System.Diagnostics.DebuggableAttribute>。  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">使用在实时调试  
 本部分演示一个可执行文件引发异常时，会发生什么情况。  
  
 你必须安装 Visual Studio 才能执行这些步骤。 如果你没有 Visual Studio，你可以下载免费[Visual Studio Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)。  
  
 请确保该实时调试是[启用](#BKMK_Enabling)。
  
 对于本部分，我们将在引发的 Visual Studio 中进行的 C# 控制台应用[NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a)。  
  
 在 Visual Studio 中，创建 C# 控制台应用程序 (**文件 > 新建 > 项目 > Visual C# > 控制台应用程序**) 名为**ThrowsNullException**。 有关在 Visual Studio 中创建项目的详细信息，请参阅[演练： 创建简单的应用程序](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。  
  
 当在 Visual Studio 中打开项目时，打开 Program.cs 文件。 将 main （） 方法替换为以下代码，也不能打印到控制台行引发 NullReferenceException，然后：  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  为了使此过程中的工作[发布配置](../debugger/how-to-set-debug-and-release-configurations.md)，你需要关闭[仅我的代码](../debugger/just-my-code.md)。 在 Visual Studio 中，单击**工具 > 选项**。 在**选项**对话框中，选择**调试**。 删除从检查**启用 ' 仅我的代码**。  
  
 生成解决方案 (在 Visual Studio 中，选择**生成 > 重新生成解决方案**)。 你可以选择调试或发布配置 (选择**调试**完整的调试体验)。 有关生成配置的详细信息，请参阅[了解生成配置](../ide/understanding-build-configurations.md)。  
  
 生成过程创建可执行 ThrowsNullException.exe。 你可以在其中创建 C# 项目的文件夹下找到它： **...\ThrowsNullException\ThrowsNullException\bin\Debug**或**...\ThrowsNullException\ThrowsNullException\bin\Release**。  
  
 双击 ThrowsNullException.exe。 你应看到如下命令窗口：  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 几秒钟后将出现一个错误窗口：  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 不要单击**取消**！ 几秒钟后，你应看到两个按钮，**调试**和**关闭程序**。 单击**调试**。  
  
> [!CAUTION]
>  如果你的应用程序包含不受信任的代码，将显示一个包含一条安全警告对话框。 此对话框使可以决定是否继续调试。 在继续调试之前，请决定你是否信任相应代码。 代码是你自己编写的吗？ 你是否信任代码编写者？ 如果该应用程序正在远程计算机上运行，你是否认识进程的名称？ 即便该应用程序在本地运行，也不一定表示它是可信的应用程序。 请考虑在计算机上运行的恶意代码的可能性。 如果你决定，则您将要调试值得信任，请单击**调试**。 否则，请单击**不调试**。  
  
 **Visual Studio 实时调试器**窗口将显示：  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 下**可能的调试器**，您应该会看到**Microsoft Visual Studio 的新实例<available version>**选择行。 如果已选中，请现在将其选中。  
  
 在窗口的底部下**你想要调试使用选定的调试器？**，单击**是**。  
  
 ThrowsNullException 项目将打开 Visual Studio 的新实例中具有执行已停止，在引发异常的行：  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 你可以开始在此时调试。 如果这是实际的应用程序，你需要找出原因代码引发异常。  
  
## <a name="just-in-time-debugging-errors"></a>实时调试错误  
 如果看不到对话框中，此程序发生故障时，这可能会由于你计算机上的 Windows 错误报告设置。 有关详细信息，请参阅[。WER 设置](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started)。  
  
 你可能会遇到与实时调试相关联的下列错误消息。  
  
-   **无法附加到崩溃进程。指定的程序不是 Windows 或 MS-DOS 程序。**  
  
     当你尝试附加到以其他用户身份运行的进程时，将出现此错误。  
  
     若要解决此问题，请启动 Visual Studio 中，打开**附加到进程**对话框**调试**菜单，然后查找的进程你想要调试在**可用进程**列表。 如果不知道该进程的名称，看看**Visual Studio 实时调试器**对话框并记下进程 id。 中选择进程**可用进程**列表，然后单击**附加**。 在**Visual Studio 实时调试器**对话框中，单击**否**以关闭对话框。  
  
-   **无法启动调试器，因为没有用户登录。**  
  
     在没有用户登录到控制台的计算机中，如果实时调试尝试启动 Visual Studio，则会发生此错误。 因为没有用户登录，所以没有用户会话来显示“实时调试”对话框。  
  
     要解决此问题，请登录到计算机。  
  
-   **未注册的类。**  
  
     此错误指出：调试器尝试创建一个可能是因为安装问题而没有注册的 COM 类。  
  
     若要解决此问题，请使用安装盘重新安装或修复 Visual Studio 安装。  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/debugger-basics.md) （调试器基础知识）  
 [在实时，调试，选项对话框](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [安全警告：附加到不受信任的用户所拥有的进程可能很危险。如果以下信息看上去可疑或者你无法确定，请勿附加到此进程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)