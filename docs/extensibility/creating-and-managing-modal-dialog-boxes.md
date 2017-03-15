---
title: "创建和管理有模式对话框 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
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
ms.openlocfilehash: 1bb0372ab217847f91b1cdeeb8cf2915379e2f66
ms.lasthandoff: 02/22/2017

---
# <a name="creating-and-managing-modal-dialog-boxes"></a>创建和管理有模式对话框
在创建模式对话框在 Visual Studio 时，您必须确保显示对话框中，同时禁用对话框中的父窗口，然后对话框中关闭后重新启用父窗口。 如果不这样做，可能会收到错误:"Microsoft Visual Studio 不能关闭，因为模式对话框处于活动状态。 关闭活动对话框，然后重试。"  
  
 有两种方法执行此操作。 建议的方法，如果您有 WPF 对话框中，是派生它从<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，然后调用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>以显示对话框。</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 如果这样做，您不需要管理模式的父窗口的状态。  
  
 如果您的对话框不是 WPF 中，或者对于某些其他原因不能派生您的对话框类派生<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>，则必须通过调用获取对话框中的父<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>自行和管理模式状态，通过调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>参数为 0 (false) 在显示对话框中，并关闭该对话框之后调用该方法再次使用的参数 1 (true) 之前的方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>创建对话框派生自 DialogWindow  
  
1.  创建一个名为的 VSIX 项目**OpenDialogTest**并添加一个名为的菜单命令**OpenDialog**。 有关如何执行此操作的详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  若要使用<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>类，必须添加对下列程序集引用 (在框架选项卡的**添加引用**对话框中):</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  在 OpenDialog.cs，添加以下`using`语句︰  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  声明一个名为类**TestDialogWindow**派生自<xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>::</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  若要能够降至最低并最大化对话框中，将设置<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>和<xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>为 true:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  在**OpenDialog.ShowMessageBox**方法中，将现有代码替换为以下︰  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  生成并运行应用程序。 Visual Studio 的实验实例应显示。 在**工具**的实验实例中的菜单上，您应该看到名为命令**调用 OpenDialog**。 当您单击此命令时，你应看到对话框窗口。 您应能够降至最低并最大化窗口。  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>创建和管理一个对话框，不是派生自 DialogWindow  
  
1.  对于此过程中，您可以使用**OpenDialogTest**在具有相同的程序集引用的上一个过程中创建的解决方案。  
  
2.  将以下代码添加`using`声明︰  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  创建一个名为类**TestDialogWindow2**派生自<xref:System.Windows.Window>::</xref:System.Windows.Window>  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  添加到<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>私有引用  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  添加设置到<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>引用一个构造函数  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  在**OpenDialog.ShowMessageBox**方法中，将现有代码替换为以下︰  
  
    ```c#  
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
  
7.  生成并运行应用程序。 在**工具**菜单上，您应该看到名为命令**调用 OpenDialog**。 当您单击此命令时，你应看到对话框窗口。
