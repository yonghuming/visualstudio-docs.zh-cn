---
title: "演练： 调试 Windows 窗体 |Microsoft 文档"
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
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a21450dda35addae55019545d67ab7f1e4ebe99a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-a-windows-form"></a>演练：调试 Windows 窗体
Windows 窗体是最常见的托管应用程序之一。 Windows 窗体创建标准的 Windows 应用程序。 你可以完成本演练使用 Visual Basic、 C# 或 c + +。  
  
 首先，您必须关闭任何打开的解决方案。  
  
### <a name="to-prepare-for-this-walkthrough"></a>准备此次演练  
  
-   如果你已经打开，将其关闭打开的解决方案。 (在**文件**菜单上，选择**关闭解决方案**。)  
  
## <a name="create-a-new-windows-form"></a>创建新的 Windows 窗体  
 接下来，你将创建一个新的 Windows 窗体。  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>若要创建本演练中的 Windows 窗体  
  
1.  上**文件**菜单上，选择**新建**单击**项目**。  
  
     此时将出现 “新建项目” 对话框。  
  
2.  在项目类型窗格中，打开**Visual Basic**， **Visual C#**，或**Visual c + +**节点，然后  
  
    1.  对于 Visual Basic 或 Visual C# 中，选择**Windows**节点，然后选择**Windows 窗体应用程序**中**模板**窗格。  
  
    2.  对于 Visual c + + 中，选择**CLR**节点，然后选择**Windows 窗体应用程序**中**模板**窗格...  
  
3.  在**模板**窗格中，选择**Windows 应用程序**。  
  
4.  在**名称**框中，为项目指定唯一的名称 (例如，Walkthrough_SimpleDebug)。  
  
5.  单击“确定”。  
  
     Visual Studio 创建一个新项目，并在 Windows 窗体设计器中显示一个新的窗体。 有关详细信息，请参阅[Windows 窗体设计器](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)。  
  
6.  上**视图**菜单上，选择**工具箱**。  
  
     随即将打开工具箱。 有关详细信息，请参阅[工具箱](../ide/reference/toolbox.md)。  
  
7.  在工具箱中，单击**按钮**控件并将控件拖动到窗体设计图面。 将按钮拖动窗体上。  
  
8.  在工具箱中，单击**文本框中**控件并将控件拖动到窗体设计图面。 删除**文本框中**窗体上。  
  
9. 在窗体设计图面上，双击按钮。  
  
     这将使你的代码页。 光标应位于`button1_Click`。  
  
10. 在函数中`button1_Click`。，添加以下代码：  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. 上**生成**菜单上，选择**生成解决方案**。  
  
     项目应顺利生成，没有错误。  
  
## <a name="debug-your-form"></a>调试窗体  
 现在，你已准备好开始调试。  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>若要调试在本演练中创建的 Windows 窗体  
  
1.  在源窗口中，单击你添加的文本的同一行的左侧的空白：  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     出现一个红点并且该行上的文本突出显示为红色。 红点表示一个断点。 有关详细信息，请参阅[断点](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)。 当你在调试器下运行该应用程序时，此调试器将在命中该代码时在该位置中断执行。 然后您可以查看应用程序的状态并调试它。  
  
    > [!NOTE]
    >  此外可以右键单击任意行的代码中，依次指向**断点**，然后单击**插入断点**该行上添加断点。  
  
2.  ON**调试**菜单上，选择**启动**。  
  
     Windows 窗体将开始运行。  
  
3.  在 Windows 窗体上，单击你添加的按钮。  
  
     在 Visual Studio 中，将转到行的代码页在其中设置断点。 该行将用黄色突出显示。 现在，可以查看应用程序中的变量并控制其执行。 你的应用程序现已停止执行，并等待从你的操作。  
  
4.  上**调试**菜单上，选择**Windows**，然后**监视**，然后单击**Watch1**。  
  
5.  在**Watch1**窗口中，单击一个空行。 在**名称**列中，键入`textBox1.Text`（如果你正在使用 Visual Basic、 Visual C# 或 J#） 或`textBox1->Text`（如果正在使用 c + +），然后按 ENTER。  
  
     **Watch1**窗口用引号括起来，作为显示此变量的值：  
  
    ```  
    ""  
    ```  
  
6.  上**调试**菜单上，选择**单步执行**。  
  
     值中的 textBox1.Text 更改**Watch1**窗口：  
  
    ```  
    Button was clicked!  
    ```  
  
7.  上**调试**菜单上，选择**继续**继续调试程序。  
  
8.  在 Windows 窗体中，请再次单击按钮。  
  
     Visual Studio 将中断再次执行。  
  
9. 单击红点表示断点。  
  
     这将在代码中移除该断点。  
  
10. 上**调试**菜单上，选择**停止调试**。  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>将附加到 Windows 窗体应用程序进行调试  
 在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中，可以将调试器附加到正在运行的进程上。 如果你在使用 Express Edition，不支持此功能。  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>若要附加的 Windows 窗体应用程序进行调试  
  
1.  在上述步骤中创建的项目中，单击左空白处来再次添加的行处设置断点：  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  上**调试**菜单上，选择**启动但不调试**。  
  
     Windows 窗体将开始运行在 Windows 下，就像已双击其可执行文件。 未附加调试器。  
  
3.  上**调试**菜单上，选择**附加到进程**。 (此命令，还可以在**工具**菜单。)  
  
     出现 **“附加到进程”** 对话框。  
  
4.  在**可用进程**窗格中，查找过程中的名称 (Walkthrough_SimpleDebug.exe)**过程**列并单击它。  
  
5.  单击**附加**按钮。  
  
6.  在 Windows 窗体中，单击是和仅按钮。  
  
     调试器在断点处中断的 Windows 窗体的执行。  
  
## <a name="see-also"></a>另请参阅  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [调试器安全](../debugger/debugger-security.md)