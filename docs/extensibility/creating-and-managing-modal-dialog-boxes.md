---
title: "创建和管理有模式对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 466f39ea7ea4b7d5b79901b2503622d2248bb7a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>创建和管理有模式对话框
在创建模式对话框在 Visual Studio 时，你必须确保当显示对话框中，禁用对话框中的父窗口，然后对话框关闭后重新启用父窗口。 如果不这样做，可能会收到错误:"Microsoft Visual Studio 无法关闭，因为一个模式对话框处于活动状态。 关闭 active 对话框中，然后重试。"  
  
 有两种方法执行此操作。 建议的方法，如果你有 WPF 对话框中，是从它派生<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，然后调用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>以显示对话框。 如果这样做，你不需要管理父窗口的模式状态。  
  
 如果对话框不是 WPF 中，或者某些其他原因无法派生对话框类从<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，则必须通过调用获取对话框中的父<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>自行和管理模式状态，通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>方法在显示对话框中，并关闭对话框之后调用再次带有 1 (true) 的参数的方法之前的 0 (false) 参数。  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>创建对话框从 DialogWindow 派生  
  
1.  创建一个名为的 VSIX 项目**OpenDialogTest**并添加名为菜单命令**OpenDialog**。 有关如何执行此操作的详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  若要使用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>类，你必须添加对以下程序集的引用 (在的框架选项卡**添加引用**对话框中):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  在 OpenDialog.cs，添加以下`using`语句：  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  声明一个名为类**TestDialogWindow**派生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  若要能够最小化和最大化对话框中，设置<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>和<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>为 true:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  在**OpenDialog.ShowMessageBox**方法，将现有代码替换为以下：  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  生成并运行应用程序。 应显示 Visual Studio 的实验实例。 上**工具**的实验实例中的菜单，您应该看到名为命令**调用 OpenDialog**。 单击此命令时，你应看到对话框窗口。 你应能够最小化和最大化窗口。  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>创建和管理不派生自 DialogWindow 对话框  
  
1.  对于此过程中，你可以使用**OpenDialogTest**在具有相同的程序集引用的上一个过程中创建的解决方案。  
  
2.  添加以下`using`声明：  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  创建一个名为类**TestDialogWindow2**派生自<xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  添加对的私有引用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  添加将引用设置为一个构造函数<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  在**OpenDialog.ShowMessageBox**方法，将现有代码替换为以下：  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  生成并运行应用程序。 上**工具**菜单您应该看到名为命令**调用 OpenDialog**。 单击此命令时，你应看到对话框窗口。