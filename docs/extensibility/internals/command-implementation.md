---
title: "命令实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0128db8288f83ab09ffe82acd66431ea6ed9da1a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="command-implementation"></a>命令实现
若要在 VSPackage 实现命令，必须执行以下任务：  
  
1.  .Vsct 文件中设置了一个命令组，然后将该命令添加到它。 有关详细信息，请参阅[Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
  
2.  注册 Visual Studio 命令。  
  
3.  实现该命令。  
  
 以下各节说明如何注册和实现命令。  
  
## <a name="registering-commands-with-visual-studio"></a>注册 Visual Studio 命令  
 如果你的命令是显示在菜单上，你必须添加<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>到你的 VSPackage，然后使用作为值的菜单名称或其资源 id。  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 此外，你必须注册该命令与<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。 你可以通过使用来获取此服务<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>方法如果你的 VSPackage 派生自<xref:Microsoft.VisualStudio.Shell.Package>。  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>实现命令  
 有多种方式来实现命令。 如果你想静态菜单命令，这是一个可始终显示相同方式和同一菜单上的命令，通过使用创建命令<xref:System.ComponentModel.Design.MenuCommand>中上一节中的示例所示。 若要创建静态命令，必须提供事件处理程序，它负责执行命令。 由于该命令始终启用且可见，你无需向 Visual Studio 中提供其状态。 如果你想要更改根据某些条件命令的状态，则可以实例的形式创建命令<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>类，并在其构造函数，提供事件处理程序以执行该命令和查询状态处理程序来通知 VisualStudio 命令的状态更改时。 你也可以实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>因为命令类或的一部分，你可以实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>如果你要作为项目的一部分提供的命令。 两个接口和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>类所有具有通知 Visual Studio 命令的状态的更改的方法和其他方法，都将执行该命令。  
  
 当命令添加到命令服务时，它将成为一个命令的链。 在实现该命令的状态通知和执行方法时，注意仅针对该特定命令提供并将链中传递到其他命令的所有其他情况。 如果您不能将命令传递上 (通常通过返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)，Visual Studio 可能会停止正常工作。  
  
## <a name="query-status-methods"></a>查询状态方法  
 如果你要实现或者<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>方法、 检查有无的命令集命令所属的 GUID 和命令 ID。 请遵循这些指导：  
  
-   如果无法识别的 GUID，任何一种方法的实现必须返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
-   如果任何一种方法的实现可识别 GUID，但不是实际实现了该命令，则该方法应返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
-   如果任何一种方法的实现可识别的 GUID 和命令，则该方法应设置每个命令的命令标志字段 (在`prgCmds`参数) 使用以下标记：  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果支持该命令。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令不应为可见。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令将打开并显示为具有已检查。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果启用了该命令。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令应被隐藏，如果它显示在快捷菜单。  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令是菜单控制器，并且未启用，但其下拉列表菜单列表不为空且仍然可用。 （此标志很少使用。）  
  
-   如果在.vsct 文件中定义该命令`TextChanges`标志，请将以下参数：  
  
    -   设置`rgwz`元素`pCmdText`命令的新文本的参数。  
  
    -   设置`cwActual`元素`pCmdText`命令字符串的大小参数。  
  
 此外请确保当前上下文不是一个自动化的函数，，除非你的命令专门用于处理自动化功能。  
  
 若要显示支持特定的命令，返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。 所有其他命令，请返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
 在下面的示例中，查询状态方法首先确保上下文不是一个自动化的函数，然后查找正确的命令集 GUID 和命令 id。 命令本身设置为处于启用状态并支持。 不支持任何其他命令。  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>执行方法  
 在执行方法的实现类似于查询状态方法实现。 首先，请确保上下文不是一个自动化函数。 然后测试的 GUID 和命令 id。 如果 GUID 或无法识别命令 ID，则返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。  
  
 若要处理命令，执行它，并返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>如果执行成功。 你的命令负责错误检测和通知;如果执行将失败，因此，返回错误代码。 下面的示例演示应如何实现执行方法。  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)