---
title: "扩展输出窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "输出窗口中的关于输出窗口"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 扩展输出窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**输出** 窗口是一组的读\/写文本窗格。 Visual Studio 提供了这些内置窗格: **生成**, ，有关生成，消息通信中的项目和 **常规**, ，在其中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将有关 IDE 的消息传递。 项目将获得对引用 **生成** 窗格中会自动通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 接口方法和 Visual Studio 提供了直接访问 **常规** 窗格中，通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> 服务。 除了内置的窗格中，您可以创建和管理您自己的自定义窗格。  
  
 您可以控制 **输出** 窗口直接通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 接口。<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 接口，提供的 <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> 服务，定义用于创建、 检索和销毁方法 **输出** 窗口窗格。<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 接口定义用于显示窗格、 隐藏窗格，和操作其文本的方法。 控制的一种替代方式 **输出** 窗口是通过 <xref:EnvDTE.OutputWindow> 和 <xref:EnvDTE.OutputWindowPane> Visual Studio 自动化对象模型中的对象。 这些对象将封装几乎所有的功能 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> 接口。 此外， <xref:EnvDTE.OutputWindow> 和 <xref:EnvDTE.OutputWindowPane> 对象添加一些更高级别的功能，以便更加轻松地枚举 **输出** 窗口窗格并从窗格中检索文本。  
  
## 创建扩展使用输出窗格  
 您可以练习输出窗格中的不同方面的扩展。  
  
1.  创建一个名为的 VSIX 项目 `TestOutput` 与菜单命令名为 **TestOutput**。 有关更多信息，请参见[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  添加以下引用:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  在 TestOutput.cs，添加以下 using 语句:  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  在 TestOutput.cs，删除 ShowMessageBox 方法。 添加以下方法存根 \(stub\):  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  TestOutput 构造函数中，将更改为 OutputCommandHandler 的命令处理程序。 下面是会将命令添加的部分:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  以下各部分具有不同显示不同的方法来处理输出窗格中的方法。 可以调用这些方法来 OutputCommandHandler\(\) 方法的主体。 例如，以下代码添加的下一节中给出的 CreatePane\(\) 方法。  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## 使用 IVsOutputWindow 创建一个输出窗口  
 此示例演示如何创建一个新 **输出** 窗口窗格中，通过使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> 接口。  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 如果将此方法添加到给定的前面部分中，当您单击扩展 **调用 TestOutput** 命令应看到 **输出** 窗口使用标头指出 **显示输出来源: CreatedPane** 和文字 **这是创建窗格中** 本身的窗格中。  
  
## 使用 OutputWindow 创建一个输出窗口  
 此示例演示如何创建 **输出** 窗口窗格中，通过使用 <xref:EnvDTE.OutputWindow> 对象。  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 尽管 <xref:EnvDTE.OutputWindowPanes> 集合使你能够检索 **输出** 窗口窗格中，通过其标题，窗格标题不能保证是唯一的。 当您不能确定一个标题的唯一性时，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> 方法来检索由其 GUID 正确窗格。  
  
 如果将此方法添加到给定的前面部分中，当您单击扩展 **调用 TestOutput** 您应该看到使用标头指出输出窗口的命令 **显示输出来源: DTEPane** 和文字 **添加 DTE 窗格** 本身的窗格中。  
  
## 删除一个输出窗口  
 此示例演示如何删除 **输出** 窗口窗格。  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 如果将此方法添加到给定的前面部分中，当您单击扩展 **调用 TestOutput** 您应该看到使用标头指出输出窗口的命令 **显示输出来源: 新窗格** 和文字 **添加创建窗格** 本身的窗格中。 如果您单击 **调用 TestOutput** 命令同样，窗格中删除。  
  
## 获取常规窗格中的输出窗口  
 此示例演示如何获取内置 **常规** 窗格 **输出** 窗口。  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 如果将此方法添加到给定的前面部分中，当您单击扩展 **调用 TestOutput** 命令您应该会看到 **输出** 窗口显示单词 **找到常规窗格** 在窗格中。  
  
## 获取生成窗格中的输出窗口  
 此示例演示如何查找生成窗格中，并向其中写入数据。 由于默认情况下，不激活生成窗格中，则会激活它还。  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```