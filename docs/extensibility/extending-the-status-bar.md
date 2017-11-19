---
title: "扩展状态栏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e170edf941455dd21727628c2e07a836db919d0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-status-bar"></a>扩展状态栏
可用于 Visual Studio 状态栏在 IDE 底部显示的信息。  
  
 扩展状态栏时，你可以在四个区域中显示信息和用户界面： 反馈区域、 进度栏、 动画区域和设计器区域。 反馈区域可以显示文本并突出显示所显示的文本。 进度栏显示等保存文件的短时间运行操作的进度。 动画区域将显示为长时间运行操作或无法确定长度没有限制，如生成的解决方案中的多个项目的操作持续闭合动画。 和设计器区域显示的光标位置的行和列数。  
  
 你可以通过使用获取状态栏<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>接口 (从<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>服务)。 此外，在窗口框架上放置的任何对象可以将注册为状态栏客户端对象通过实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>接口。 Visual Studio 窗口被激活，每当查询放置在该窗口的对象`IVsStatusbarUser`接口。 如果找到，则会调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法返回的接口和对象可以更新状态栏从该方法中的。 文档窗口，例如，可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法来更新设计器区域中的信息时它们变为活动状态。  
  
 以下过程假设你了解如何创建一个 VSIX 项目并添加一个自定义菜单命令。 有关信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## <a name="modifying-the-status-bar"></a>修改状态栏  
 此过程演示如何设置和获取文本、 显示静态文本，并突出显示状态栏的反馈区域中显示的文本。  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>读取和写入到状态栏  
  
1.  创建一个名为的 VSIX 项目**TestStatusBarExtension**并添加名为菜单命令**TestStatusBarCommand**。  
  
2.  在 TestStatusBarCommand.cs，将替换为以下的命令处理程序方法代码 (MenuItemCallback):  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  编译代码并开始调试。  
  
4.  打开**工具**Visual Studio 的实验实例中的菜单。 单击**调用 TestStatusBarCommand**按钮。  
  
     您应该会看到现在读取状态栏中的文本**"我们刚刚已写入到状态栏。"** 并且，显示的消息框中具有相同的文本。  
  
#### <a name="updating-the-progress-bar"></a>更新进度栏  
  
1.  在此过程中，我们将演示如何初始化和更新进度栏。  
  
2.  打开 TestStatusBarCommand.cs 文件和 MenuItemCallback 方法替换为以下代码：  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  编译代码并开始调试。  
  
4.  打开**工具**Visual Studio 的实验实例中的菜单。 单击**调用 TestStatusBarCommand**按钮。  
  
     您应该会看到现在读取状态栏中的文本**"编写与进度栏。"** 你应看到进度栏会更新每隔一秒 20 秒。 在此之后清除状态栏，进度栏。  
  
#### <a name="displaying-an-animation"></a>显示动画  
  
1.  状态栏会显示循环的动画指示 （例如，生成的解决方案中的多个项目） 的长时间运行操作。 如果看不到此动画，请确保你有正确**工具 / 选项**设置：  
  
     转到**工具/选项 / 常规**选项卡上，并取消选中**自动调整视觉体验基于客户端性能**。 然后检查子选项**启用丰富客户端视觉体验**。 你现在应能够生成你的 Visual Studio 的实验实例中的项目时，请参阅动画。  
  
     在此过程中，我们将显示标准的 Visual Studio 动画，它表示生成项目或解决方案。  
  
2.  打开 TestStatusBarCommand.cs 文件和 MenuItemCallback 方法替换为以下代码：  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  编译代码并开始调试。  
  
4.  打开**工具**在实验实例中的 Visual Studio 和单击菜单**调用 TestStatusBarCommand**。  
  
     当你看到此消息框时，您还会在最右侧看到状态栏中的动画。 关闭该消息框，就会消失动画。