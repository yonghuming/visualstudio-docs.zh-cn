---
title: "扩展输出窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e183413446bbca2ffed0642619ab63538fae0f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-output-window"></a>扩展输出窗口
**输出**窗口是一套读/写文本窗格。 Visual Studio 具有这些内置窗格：**生成**中的项目进行通信有关生成、 消息和**常规**，在其中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]将有关 IDE 的消息传递。 项目获取的引用**生成**窗格自动通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>接口方法和 Visual Studio 提供了直接访问**常规**窗格中，通过<xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane>服务。 除了内置的窗格中，你可以创建和管理你自己的自定义窗格。  
  
 你可以控制**输出**窗口直接通过<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>接口。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>接口，所提供的<xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow>服务、 定义方法创建、 检索和销毁**输出**窗口窗格。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>接口定义用于显示窗格、 隐藏窗格，和操作其文本的方法。 替代方式的控制**输出**窗口是通过<xref:EnvDTE.OutputWindow>和<xref:EnvDTE.OutputWindowPane>Visual Studio 自动化对象模型中的对象。 这些对象将封装的功能的几乎所有<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>接口。 此外，<xref:EnvDTE.OutputWindow>和<xref:EnvDTE.OutputWindowPane>对象添加一些更高级别的的功能，以更加轻松地枚举**输出**窗口窗格和以检索从窗格的文本。  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>创建扩展来使用输出窗格  
 你可以执行的输出窗格中的不同方面的扩展。  
  
1.  创建一个名为的 VSIX 项目`TestOutput`菜单命令与名为**TestOutput**。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  添加以下引用：  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  在 TestOutput.cs，添加以下 using 语句：  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  在 TestOutput.cs，删除 ShowMessageBox 方法。 添加以下方法存根 （stub）：  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  在 TestOutput 构造函数将更改为 OutputCommandHandler 的命令处理程序。 下面是将命令添加的部分：  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  下面的部分具有显示不同的方法来处理输出窗格中的不同方法。 可以调用这些方法来 OutputCommandHandler() 方法的主体。 例如，以下代码添加下一节中给出的 CreatePane() 方法。  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>使用 IVsOutputWindow 创建输出窗口  
 此示例演示如何创建一个新**输出**窗口窗格中，通过使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>接口。  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 如果将此方法添加到当你单击在上一部分中，给定扩展**调用 TestOutput**命令你应该会看到**输出**使用显示的标头的窗口**显示输出从： CreatedPane**和文字**这是创建窗格**本身的窗格中。  
  
## <a name="creating-an-output-window-with-outputwindow"></a>使用 OutputWindow 创建输出窗口  
 此示例演示如何创建**输出**窗口窗格中，通过使用<xref:EnvDTE.OutputWindow>对象。  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 尽管<xref:EnvDTE.OutputWindowPanes>集合使你能够检索**输出**按其标题的窗口窗格中，窗格标题不保证是唯一的。 当你怀疑标题的唯一性时，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A>方法来检索由其 GUID 正确窗格。  
  
 如果将此方法添加到当你单击在上一部分中，给定扩展**调用 TestOutput**你应看到使用标头显示输出窗口的命令**显示以下输出： DTEPane**和单词**添加 DTE 窗格**本身的窗格中。  
  
## <a name="deleting-an-output-window"></a>删除输出窗口  
 此示例演示如何删除**输出**窗口窗格。  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 如果将此方法添加到当你单击在上一部分中，给定扩展**调用 TestOutput**你应看到使用标头显示输出窗口的命令**显示以下输出： 新窗格**和单词**添加创建窗格**本身的窗格中。 如果你单击**调用 TestOutput**再次，命令删除窗格。  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>获取输出窗口的常规窗格中  
 此示例演示如何获取内置**常规**窗格**输出**窗口。  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 如果将此方法添加到当你单击在上一部分中，给定扩展**调用 TestOutput**命令您应该会看到**输出**窗口显示单词**找到常规窗格**在窗格中。  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>获取输出窗口的生成窗格中  
 此示例演示如何查找生成窗格并向其中写入。 由于默认情况下未激活生成窗格中，则会激活它还。  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```