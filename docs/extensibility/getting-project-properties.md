---
title: "获取项目属性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 09a811a3bb42f5de9406ec85038579b5545619ae
ms.lasthandoff: 02/22/2017

---
# <a name="getting-project-properties"></a>获取项目属性
本演练演示如何在一个工具窗口中显示项目属性。  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>若要创建 VSIX 项目并添加一个工具窗口  
  
1.  每个 Visual Studio 的扩展从一个 VSIX 部署项目，它将包含的扩展资产开始。 创建[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 项目名为`ProjectPropertiesExtension`。 您可以找到中的 VSIX 项目模板**新项目**下的对话框**Visual C# / 可扩展性**。  
  
2.  通过添加一个名为的自定义工具窗口项模板添加一个工具窗口`ProjectPropertiesToolWindow`。 在**解决方案资源管理器**，用鼠标右键单击项目节点并选择**添加 / 新项**。 在**添加新项对话框**，请转到**Visual C# 项 / 扩展性**，然后选择**自定义工具窗口**。 在**名称**在对话框底部字段中，文件将名称更改为`ProjectPropertiesToolWindow.cs`。 有关如何创建自定义工具窗口的详细信息，请参阅[使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  生成解决方案并确认编译时不会产生错误。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>若要在工具窗口中显示项目属性  
  
1.  在 ProjectPropertiesToolWindowCommand.cs 文件中添加以下 using 语句。  
  
    ```c#  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  在 ProjectPropertiesToolWindowControl.xaml，删除现有的按钮，并从工具箱添加树视图。 此外可以从 ProjectPropertiesToolWindowControl.xaml.cs 文件删除 click 事件处理程序。  
  
3.  在 ProjectPropertiesToolWindowCommand.cs，使用 ShowToolWindow() 方法打开该项目并读取其属性，然后将属性添加到树视图。 ShowToolWindow 的代码应如下所示︰  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  生成项目并启动调试。 应显示的实验实例。  
  
5.  在实验实例中打开一个项目。  
  
6.  在**视图 / 其他窗口**单击**ProjectPropertiesToolWindow**。  
  
     您应该看到工具窗口中名称的第一个项目及它的所有项目属性的名称以及在树控件。
