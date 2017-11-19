---
title: "创建多实例工具窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4dd74bc1a59d93e2eef9c7dc00d8b83d53628a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-multi-instance-tool-window"></a>创建多实例工具窗口
以便它的多个实例可以同时打开工具窗口，您可以对其进行编程。 默认情况下，工具窗口只能有一个打开的实例。  
  
 使用多实例工具窗口时，可以显示在同一时间的信息的多个相关的来源。 例如，您可以将多行<xref:System.Windows.Forms.TextBox>控制在多实例工具窗口中，以便多个代码段编程会话中均同时可用。 此外例如中，你可能会使<xref:System.Windows.Forms.DataGrid>控件和下拉列表框中的多实例工具窗口，以便可以同时跟踪多个实时数据源。  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>创建 Basic （单实例） 工具窗口  
  
1.  创建一个名为项目**MultiInstanceToolWindow**使用 VSIX 模板，并添加名为的自定义工具窗口项模板**MIToolWindow**。  
  
    > [!NOTE]
    >  有关使用工具窗口创建扩展的详细信息，请参阅[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="making-a-tool-window-multi-instance"></a>从而使工具窗口多实例  
  
1.  打开**MIToolWindowPackage.cs**文件并查找`ProvideToolWindow`属性。 与`MultiInstances=true`参数，如下面的示例中所示。  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  在 MIToolWindowCommand.cs 文件中查找 ShowToolWindos() 方法。 在此方法，调用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法并设置其`create`标志切换为`false`，以便它将循环访问现有的工具窗口实例之前可用`id`找到。  
  
3.  若要创建工具窗口实例，请调用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法并设置其`id`为可用的值并将其`create`标志切换为`true`。  
  
     默认情况下，值`id`参数<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法是`0`。 这使得单实例工具窗口。 对于要承载的多个实例，每个实例必须具有其自己唯一`id`。  
  
4.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>返回的对象<xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>的工具窗口实例的属性。  
  
5.  默认情况下，`ShowToolWindow`由工具窗口项模板创建的方法创建一个单实例工具窗口。 下面的示例演示如何修改`ShowToolWindow`方法来创建多个实例。  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```