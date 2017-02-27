---
title: "扩展状态栏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "状态栏关于状态栏"
  - "状态栏概述"
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 扩展状态栏
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可用于 Visual Studio 状态栏在 IDE 底部显示的信息。  
  
 扩展状态栏时，您可以在四个区域中显示信息和用户界面: 反馈区域、 进度栏、 动画区域和设计器区域。 反馈区域可以显示文本并突出显示所显示的文本。 进度栏显示为短时间运行操作，如保存文件的进度。 动画区域将显示为长时间运行操作或操作无法确定长度没有限制，如生成多个项目在解决方案中的一个连续循环的动画。 和设计器区域显示的光标位置的行和列数。  
  
 您可以通过使用状态栏 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口 \(从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 服务\)。 此外，在窗口框架上放置的任何对象可以通过注册为状态栏客户端对象实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 接口。 每当激活一个窗口，Visual Studio 中放置在该窗口向对象查询 `IVsStatusbarUser` 接口。 如果找到，则会调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 方法返回的接口和对象可以更新状态栏从该方法中的。 文档窗口，例如，可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 方法来更新设计器区域中的信息，它们在何时变为活动状态。  
  
 下面的过程假定您了解如何创建 VSIX 项目并添加自定义菜单命令。 有关信息，请参阅 [使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
## 修改状态栏  
 此过程演示如何设置和获取文本、 显示静态文本，并突出显示状态栏的反馈区域中显示的文本。  
  
#### 读取和写入状态栏  
  
1.  创建一个名为的 VSIX 项目 **TestStatusBarExtension** 并添加一个名为的菜单命令 **TestStatusBarCommand**。  
  
2.  在 TestStatusBarCommand.cs，替换命令处理程序方法代码 \(MenuItemCallback\) 以下内容:  
  
    ```c#  
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
  
4.  打开 **工具** Visual Studio 的实验实例中的菜单。 单击 **调用 TestStatusBarCommand** 按钮。  
  
     您应该会看到现在读取在状态栏中的文本 **"我们刚刚写入状态栏"** 并将显示该消息框具有相同的文本。  
  
#### 更新进度条  
  
1.  在此过程中，我们将演示如何初始化和更新进度条。  
  
2.  打开 TestStatusBarCommand.cs 文件，并用下面的代码替换 MenuItemCallback 方法:  
  
    ```c#  
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
  
4.  打开 **工具** Visual Studio 的实验实例中的菜单。 单击 **调用 TestStatusBarCommand** 按钮。  
  
     您应该会看到现在读取在状态栏中的文本 **"写入进度栏"**您应看到进度栏会更新每秒 20 秒。 之后，清除状态栏和进度栏。  
  
#### 显示动画  
  
1.  状态栏不显示循环的动画，该值指示是一个长时间运行的操作 \(例如，构建一个解决方案中的多个项目\)。 如果看不到此动画，请确保您具有正确 **工具 \/ 选项** 设置:  
  
     转到 **工具\/选项 \/ 常规** 选项卡上，取消选中 **自动调整视觉体验基于客户端性能**。 然后选中子选项 **启用丰富的客户端视觉体验**。 现在，您应能够生成您的 Visual Studio 的实验实例中的项目时，将显示动画。  
  
     在此过程中，我们将显示标准的 Visual Studio 动画，它表示生成项目或解决方案。  
  
2.  打开 TestStatusBarCommand.cs 文件，并用下面的代码替换 MenuItemCallback 方法:  
  
    ```c#  
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
  
4.  打开 **工具** 在实验实例中的 Visual Studio 和单击菜单 **调用 TestStatusBarCommand**。  
  
     当你看到消息框中时，您还会在最右侧看到状态栏中的动画。 关闭该消息框，动画就会消失。