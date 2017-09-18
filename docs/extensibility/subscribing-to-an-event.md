---
title: "订阅事件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
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
ms.openlocfilehash: 6bd1dd320ad5366ef494a8db958614d837529320
ms.lasthandoff: 02/22/2017

---
# <a name="subscribing-to-an-event"></a>订阅事件
本演练说明了如何创建一个工具窗口，对正在运行的 document 表 (RDT) 的事件做出响应。 工具窗口承载实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>用户控件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法连接到这些事件的接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
## <a name="prerequisites"></a>先决条件  
 启动 Visual Studio 2015 中，您并不安装 Visual Studio SDK 从下载中心获得。 它将包括作为 Visual Studio 安装程序中的可选功能。 您还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="subscribing-to-rdt-events"></a>璹綷 RDT 事件  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>若要使用的工具窗口创建扩展  
  
1.  创建一个名为项目**RDTExplorer**使用 VSIX 模板，并将添加一个名为的自定义工具窗口项模板**RDTExplorerWindow**。  
  
     有关使用一个工具窗口创建扩展的详细信息，请参阅[使用一个工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
#### <a name="to-subscribe-to-rdt-events"></a>璹綷 RDT 事件  
  
1.  打开 RDTExplorerWindowControl.xaml 文件并删除名为的按钮`button1`。 添加<xref:System.Windows.Forms.ListBox>控件并接受默认名称。</xref:System.Windows.Forms.ListBox> Grid 元素应该如下所示︰  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  在代码视图中打开 RDTExplorerWindow.cs 文件。 将以下代码添加到开始的文件的 using 语句。  
  
    ```c#  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  修改`RDTExplorerWindow`类这样，除了派生自<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>类，它实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>  
  
    -   实现接口。 将光标置于 IVsRunningDocTableEvents 名称。 您应该看到左侧边距中该变量的灯泡图标。 单击灯泡图标右侧的向下箭头，然后选择**实现接口**。  
  
5.  在接口中的每个方法，将行`throw new NotImplementedException();`与此︰  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
6.  将 cookie 字段添加到 RDTExplorerWindow 类。  
  
    ```c#  
    private uint rdtCookie;   
    ```  
  
     它将保存所返回的 cookie<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
7.  重写 RDTExplorerWindow initialize （） 方法，以注册 RDT 事件。 您始终应在 ToolWindowPane initialize （） 方法中，构造函数中不可以获得服务。  
  
    ```c#  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>服务调用以获得<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>接口。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>方法连接到一个对象，实现 RDT 事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>，在这种情况下，RDTExplorer 对象。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> </xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>  
  
8.  更新 RDTExplorerWindow 的 dispose （） 方法。  
  
    ```c#  
    protected override void Dispose(bool disposing)  
    {  
        // Release the RDT cookie.  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));  
        rdt.UnadviseRunningDocTableEvents(rdtCookie);  
  
        base.Dispose(disposing);  
    }  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>方法删除之间的连接`RDTExplorer`和 RDT 事件通知。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>  
  
9. 将以下行添加到主体<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>处理程序中，紧前面`return`语句。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>  
  
    ```c#  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. 将类似的代码行添加到主体<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>处理程序和你想要在列表框中查看其他事件。</xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>  
  
    ```c#  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. 生成项目并启动调试。 将显示 Visual Studio 实验实例。  
  
12. 打开**RDTExplorerWindow** (**视图 / 其他窗口 / RDTExplorerWindow**)。  
  
     **RDTExplorerWindow**窗口将打开与空的事件列表。  
  
13. 打开或创建一个解决方案。  
  
     作为`OnBeforeLastDocument`和`OnAfterFirstDocument`，将激发事件，通知的每个事件就会出现在事件列表。
