---
title: "在 Visual Studio 进行实时调试 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "调试 [Visual Studio], 实时"
  - "实时调试"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在 Visual Studio 进行实时调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在运行于 Visual Studio 之外的应用程序中发生异常或崩溃时，实时调试会自动启用 Visual Studio。  这样，你便可以在 Visual Studio 没有运行时测试应用程序，并在出现问题时利用 Visual Studio 开始调试。  
  
 实时调试不适用于 Windows 应用商店应用。  实时调试不适用于在可视化工具等本机应用程序中承载的托管代码。  
  
## 使用实时调试  
 默认情况下，安装 Visual Studio 时会启用实时调试。  如果您需要禁用或重新启用实时调试，请参阅[限制单步执行“仅我的代码”](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)。  
  
 启用实时调试之后，你可以在 Visual Studio 之外调试应用程序。  如果发生崩溃或异常，将会出现一个对话框，其中显示一条与下面类似的消息：  
  
 在 terrarium.exe\[3384\] 中发生未经处理的异常（“System.TypeInitializationException”）  
  
 如果出现此对话框，你可以通过以下步骤开始调试。  
  
#### 发生错误时开始实时调试  
  
1.  在“实时调试”对话框的**“可能的调试器”**列表中，单击**“Visual Studio 2015 新实例”**或单击已在运行的 Visual Studio 实例。  
  
2.  若要对所有未来的崩溃自动使用 Visual Studio，请单击**“将当前选定的调试器设置为默认调试器”**。  
  
3.  如果要选择能够调试的代码类型，请单击**“手动选择调试引擎”**。  如果没有选择此选项，Visual Studio 将根据程序中的代码类型自动选择合适的调试引擎。  
  
4.  单击“确定”。  
  
5.  如果在你的应用程序中，某个程序集包含不受信任的代码，则会出现一个对话框以及一条安全警告。  此对话框使可以决定是否继续调试。  在继续调试之前，请决定你是否信任相应代码。  代码是你自己编写的吗？  你是否信任代码编写者？  如果该应用程序正在远程计算机上运行，你是否认识进程的名称？  即便该应用程序在本地运行，也不一定表示它是可信的应用程序。  例如，在 Internet Explorer 中可能会有恶意 ActiveX 控件运行。  请考虑此类恶意代码在你的计算机中运行的可能性。  如果你确信待调试代码值得信任，请单击**“调试”**。  否则，请单击**“不调试”**。  
  
##  <a name="BKMK_Enabling"></a> 启用或禁用实时调试  
 你可以在**“选项”**对话框中启用或禁用实时调试。  
  
#### 启用或禁用实时调试  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
2.  在**“选项”**对话框中选择**“调试”**文件夹。  
  
3.  在**“调试”**文件夹中选择**“实时”**页。  
  
4.  在**“启用这些代码类型的实时调试”**框中，选中或清除相关的程序类型：**“托管”**、**“本机”**或**“脚本”**。  
  
     要在启用实时调试后禁用它，必须使用管理员特权运行。  启用实时调试会设置一个注册表项，需要管理员特权才可以更改该项。  
  
5.  单击“确定”。  
  
 默认情况下，Windows 窗体应用程序有一个顶级的异常处理程序，该处理程序允许程序在能够恢复时继续运行。  因此，若要启用 Windows 窗体应用程序的实时调试，还必须执行下列步骤。  
  
#### 为 Windows 窗体启用实时调试  
  
1.  在 machine.config 或 `jitDebugging`application.exe.config 文件的 `true` 部分中，将 `system.windows.form` 值设置为 *：*  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  在 C\+\+ Windows 窗体应用程序中，还必须在 .config 文件或你的代码中设置 `DebuggableAttribute`。  如果在编译时使用 [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) 而没有使用 [\/Og](/visual-cpp/build/reference/og-global-optimizations)，则编译器会替你设置此特性。  然而，如果你想要调试非优化发布版本，则必须自行设置此项。  为此，你可以在应用程序的 AssemblyInfo.cpp 文件中添加下面一行：  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     有关详细信息，请参阅<xref:System.Diagnostics.DebuggableAttribute>。  
  
 即便在你的计算机中不再安装有 Visual Studio，仍可启用实时调试。  如果没有安装 Visual Studio，则不能在 Visual Studio**“选项”**对话框中禁用实时调试。  对于这种情况，你可以通过编辑 Windows 注册表来禁用实时调试。  
  
#### 通过编辑注册表禁用实时调试  
  
1.  在**“开始”**菜单上，搜索并运行 `regedit.exe`  
  
2.  在**“注册表编辑器”**窗口中，找到并删除下列注册表项：  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  如果你的计算机运行的是 64 位操作系统，还请删除下列注册表项：  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  注意不要意外删除或更改任何其他注册表项。  
  
5.  关闭**“注册表编辑器”**窗口。  
  
## 实时调试错误  
 你可能会遇到与实时调试相关联的下列错误消息。  
  
-   **无法附加到崩溃进程。  指定的程序不是 Windows 或 MS\-DOS 程序。**  
  
     当你尝试附加到 Windows 2000 下作为另一个用户运行的进程时会发生该错误。  
  
     若要解决此问题，请启动 Visual Studio，从**“调试”**菜单中打开**“附加到进程”**对话框，然后在**“可用进程”**列表中查找要调试的进程。  如果你不知道进程名称，请查看**“Visual Studio 实时调试器”**对话框并记下进程 ID。  在**“可用进程”**列表中选择该进程并单击**“附加”**。  在**“Visual Studio 实时调试器”**对话框中单击**“否”**以关闭该对话框。  
  
-   **未能启动调试器，因为没有用户登录。**  
  
     在没有用户登录到控制台的计算机中，如果实时调试尝试启动 Visual Studio，则会发生此错误。  因为没有用户登录，所以没有用户会话来显示“实时调试”对话框。  
  
     要解决此问题，请登录到计算机。  
  
-   **类没有注册。**  
  
     此错误指出：调试器尝试创建一个可能是因为安装问题而没有注册的 COM 类。  
  
     若要解决此问题，请使用安装盘重新安装或修复 Visual Studio 安装。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试器基础知识](../debugger/debugger-basics.md)   
 [“选项”对话框 \-\>“调试”\-\>“实时”](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [安全警告: 附加到不受信任的用户拥有的进程可能很危险。如果下面的信息看上去可疑或无法确定，请不要附加到此进程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)