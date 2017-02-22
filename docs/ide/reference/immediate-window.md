---
title: "即时窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ImmediateWindow"
helpviewer_keywords: 
  - "设计时间表达式计算"
  - "即时窗口"
  - "及早异常通知"
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 即时窗口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

“即时”窗口用于调试和计算表达式、执行语句、输出变量值等。  它使您得以在调试期间输入表达式，由开发语言对其进行计算或执行。  若要显示“即时”窗口，请打开要编辑的项目，然后从“调试”菜单中选择“窗口”，再选择“即时”，或按 CTRL\+ALT\+I。  
  
 可以使用此窗口发出单个 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令。  可用的命令包括 `EvaluateStatement`，用于为变量赋值。  **“即时”**窗口还支持 IntelliSense。  
  
## 显示变量的值  
 此窗口在调试应用程序时特别有用。  例如，若要检查变量 `varA` 的值，可以使用 [Print 命令](../../ide/reference/print-command.md)：  
  
```  
>Debug.Print varA  
```  
  
 问号 \(?\) 是 `Debug.Print` 的别名，因此此命令还可以写为：  
  
```  
>? varA  
```  
  
 此命令的这两种版本都将返回变量 `varA` 的值。  
  
> [!NOTE]
>  若要在“即时”窗口中发出 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令，必须以大于号 \(\>\) 作为命令开头。  若要输入多个命令，请切换到**“命令”**窗口。  
  
## 设计时表达式计算  
 您可以在设计时使用**“即时”**窗口来执行函数或子例程。  
  
#### 在设计时执行函数  
  
1.  将下面的代码复制到 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 控制台应用程序中：  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  在**“调试”**菜单中单击**“窗口”**，然后单击**“即时”**。  
  
3.  在**“即时”**窗口中键入 `?MyFunction(2)`，然后按 Enter。  
  
     **“即时”**窗口将运行 `MyFunction` 并显示 `4`。  
  
 如果函数或子例程包含断点，则 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 会在适当断点处中断执行。  然后，您就可以使用调试器窗口检查您的程序状态。  有关更多信息，请参见[演练：在设计时调试](../../debugger/walkthrough-debugging-at-design-time.md)。  
  
 您不能在需要启动执行环境的项目类型（包括 [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] 项目、Web 项目、智能设备项目和 SQL 项目）中使用设计时表达式计算。  
  
### 多项目解决方案中的设计时表达式计算  
 当建立设计时表达式计算的上下文时，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 引用解决方案资源管理器中当前选择的项目。  如果没有在解决方案资源管理器中选择项目，则 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 会尝试针对启动项目计算函数。  如果不能在当前上下文中计算函数，您将收到错误消息。  如果您尝试在不是解决方案的启动项目的项目中计算函数并收到错误，请在解决方案资源管理器中选择项目，然后重新尝试计算。  
  
## 输入命令  
 必须输入大于号 \(\>\)，当在“即时”窗口发出 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令时。  使用向上键和向下键可滚动显示以前发出的命令。  
  
|任务|解决方案|示例|  
|--------|----------|--------|  
|计算表达式的值。|表达式以问号 \(?\) 开始。|`? a+b`|  
|在“即时”模式下临时进入“命令”模式（以执行单个命令）。|输入命令，在命令前面加一个大于号 \(\>\)。|`>alias`|  
|切换到“命令”窗口。|在窗口中输入 `cmd`，并在命令前面加一个大于号 \(\>\)。|`>cmd`|  
|切换回“即时”窗口。|在窗口中输入 `immed` ，不带大于号 \(\>\)。|`immed`|  
  
## 标记模式  
 在**“即时”**窗口中单击前面的任何行时，将自动切换到“标记”模式。  这允许您像在任何文本编辑器中那样选择、编辑和复制以前命令的文本，并将其粘贴到当前行中。  
  
## 等号 \(\=\)  
 用于输入 `EvaluateStatement` 命令的窗口确定是将等号 \(\=\) 解释为比较运算符还是赋值运算符。  
  
 在**“即时”**窗口中，将等号 \(\=\) 解释为赋值运算符。  例如，命令  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 将为变量 `varA` 赋予变量 `varB` 的值。  
  
 与此相反，在**“命令”**窗口中，将等号 \(\=\) 解释为比较运算符。  不能在**“命令”**窗口中进行赋值运算。  例如，如果变量 `varA` 和 `varB` 的值不相同，则命令  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 将返回 `False` 值。  
  
## 首次异常通知  
 在有些设置配置中，首次异常通知显示在**“即时”**窗口中。  
  
#### 在即时窗口中切换首次异常通知开关  
  
1.  在**“视图”**菜单上单击**“其他窗口”**，然后单击**“输出”**。  
  
2.  右击**“输出”**窗口的文本区域，然后选择或取消选择**“异常消息”**。  
  
## 请参阅  
 [使用调试器浏览代码](../../debugger/navigating-through-code-with-the-debugger.md)   
 [“命令”窗口](../../ide/reference/command-window.md)   
 [使用 Visual Studio 进行调试](../../debugger/debugging-in-visual-studio.md)   
 [调试器基础知识](../../debugger/debugger-basics.md)   
 [演练：在设计时调试](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)   
 [在 Visual Studio 中使用正则表达式](../../ide/using-regular-expressions-in-visual-studio.md)