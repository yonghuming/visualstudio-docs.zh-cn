---
title: "如何：使用“调用堆栈”窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.callstack"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "aspx"
helpviewer_keywords: 
  - "线程处理 [Visual Studio]，显示双向调用"
  - "函数 [调试器]，查看调用堆栈上的代码"
  - "反汇编代码"
  - "断点，“调用堆栈”窗口"
  - "调试 [Visual Studio]，切换到另一个堆栈帧"
  - "调试 [Visual Studio]，“调用堆栈”窗口"
  - "“调用堆栈”窗口，查看调用堆栈上的函数的源代码"
  - "堆栈，切换堆栈帧"
  - "“调用堆栈”窗口，查看调用堆栈上的函数的反汇编代码"
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用“调用堆栈”窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用**“调用堆栈”**窗口可以查看当前堆栈上的函数或过程调用。  
  
 **“调用堆栈”**窗口显示每个函数的名称以及编写它所用的编程语言。  函数或过程名称可能包含可选信息，如模块名称、行号、参数名称、类型和值。  可以打开或关闭这些可选信息的显示。  
  
 一个黄色箭头标识执行指针当前所位于的堆栈帧。  默认情况下，该帧的信息显示在源、**“反汇编”**、**“局部变量”**、**“监视”**和**“自动”**窗口中。  如果想将上下文更改为堆栈上的另一个帧，可以在**“调用堆栈”**窗口中执行相应的操作。  
  
 当调试符号对部分调用堆栈不可用时，**“调用堆栈”**窗口也许就不能显示那部分调用堆栈的正确信息。  将出现以下表示法：  
  
 \[下面的帧可能不正确和\/或缺失，没有为 name.dll 加载符号\]  
  
 在托管代码中，默认情况下，**“调用堆栈”**窗口将隐藏非用户代码的信息。  在隐藏信息处出现以下表示法：  
  
 **\[\<External Code\>\]**  
  
 非用户代码是任何代码，这些代码不是可通过快捷菜单选择以显示非用户代码的调用堆栈信息的我的代码。  
  
 可以使用快捷菜单选择查看线程之间的调用。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您的当前设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 以中断模式或运行模式显示“调用堆栈”窗口  
  
-   在**“调试”**菜单中选择**“窗口”**，然后单击**“调用堆栈”**。  
  
### 更改显示的可选信息  
  
-   右键单击**“调用堆栈”**窗口，然后设置或清除**“显示 \<***the information that you want***\>”**。  
  
### 在“调用堆栈”窗口中显示非用户代码帧  
  
-   右击**“调用堆栈”**窗口，然后选择**“显示外部代码”**。  
  
### 切换到另一个堆栈帧  
  
1.  在**“调用堆栈”**窗口中，右击要查看其代码和数据的帧。  
  
2.  选择**“切换到帧”**。  
  
     一个带有卷尾的绿色箭头显示在所选帧旁。  执行指针保留在原始帧中，仍然用黄色箭头标记。  如果从**“调试”**菜单中选择**“单步执行”**或**“继续”**，执行将继续在原始帧中进行，而不是在选定的帧中进行。  
  
### 显示与其他线程之间的来回调用  
  
-   右击**“调用堆栈”**窗口，然后选择**“包括对其他线程和来自其他线程的调用”**。  
  
### 查看调用堆栈上的函数的源代码  
  
-   在**“调用堆栈”**窗口中，右击要查看其源代码的函数，然后选择**“转到源代码”**。  
  
### 直观地跟踪调用堆栈  
  
1.  在**“调用堆栈”**窗口中，打开快捷菜单。  选择**“在代码图上显示调用堆栈”**。（键盘：**Ctrl** \+ **Shift** \+ **\`**）  
  
     请参阅[调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
### 查看调用堆栈上的函数的反汇编代码  
  
-   在**“调用堆栈”**窗口中，右击要查看其反汇编代码的函数，然后选择**“转到反汇编”**。  
  
### 从“调用堆栈”窗口运行到特定函数  
  
-   请参阅[运行至指定位置或函数](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Run_to_a_specified_location_or_function)。  
  
### 在函数调用的退出点上设置断点  
  
-   请参阅[在源行、程序集指令或调用堆栈函数处设置断点](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_at_a_source_line__assembly_instruction__or_call_stack_function_)。  
  
### 加载模块符号  
  
-   如果要重新加载模块的符号，请在**“调用堆栈”**窗口中右击显示该模块的帧，然后选择**“加载符号”**。  
  
## 加载符号  
 在**“调用堆栈”**窗口中，可以为当前还未加载符号的代码加载调试符号。  这些符号可以是从 Microsoft 公共符号服务器下载的 .NET Framework 符号或系统符号，也可以是正在调试的计算机上的某个符号路径中的符号。  
  
 请参阅[指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### 加载符号  
  
1.  在**“调用堆栈”**窗口中，右击尚未为其加载符号的帧。  此帧将显示为灰色。  
  
2.  指向**“加载符号”**，然后单击**“Microsoft 符号服务器”**或**“符号路径”**。  
  
#### 设置符号路径  
  
1.  在**“调用堆栈”**窗口中，从快捷菜单中选择**“符号设置”**。  
  
     将打开**“选项”**对话框并显示**“符号”**页。  
  
2.  单击**“符号设置”**。  
  
3.  在**“选项”**对话框中单击“文件夹”图标。  
  
     在**“符号文件\(.pdb\)位置”**框中将出现一个光标。  
  
4.  键入所调试的计算机上的符号位置的目录路径名。  对于本地调试，此计算机指您的本地计算机。  对于远程调试，此计算机指远程计算机。  
  
5.  单击**“确定”**关闭**“选项”**对话框。  
  
## 请参阅  
 [“调用堆栈”窗口中的混合代码与丢失信息](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [如何：更改调试器窗口的数字格式](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)   
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)   
 [指定符号 \(.pdb\) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [使用断点](../debugger/using-breakpoints.md)