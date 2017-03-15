---
title: "命令实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
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
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>命令实现
若要在 VSPackage 中实现命令，必须执行以下任务︰  
  
1.  在.vsct 文件中，设置了一个命令组，然后向其中添加该命令。 有关详细信息，请参阅[Visual Studio 命令表 (。Vsct) 文件](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
  
2.  注册 Visual Studio 中的命令。  
  
3.  实现该命令。  
  
 以下部分说明如何注册和实现命令。  
  
## <a name="registering-commands-with-visual-studio"></a>使用 Visual Studio 注册命令  
 如果您的命令将出现在菜单上，您必须添加<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>到你的 VSPackage，并且作为值的菜单或其资源 id。 名称的使用</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 此外，您必须向<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>注册命令 可以通过使用<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>方法，如果你的 VSPackage 派生自<xref:Microsoft.VisualStudio.Shell.Package>。</xref:Microsoft.VisualStudio.Shell.Package></xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>获取此服务  
  
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
 有多种方法来实现命令。 如果要让静态菜单命令，这是始终显示相同方式，在相同的菜单上的命令，该命令使用创建<xref:System.ComponentModel.Design.MenuCommand>中上一节中的示例所示。</xref:System.ComponentModel.Design.MenuCommand> 若要创建静态命令，您必须提供的事件处理程序负责执行该命令。 由于该命令始终启用且可见，您无需为 Visual Studio 提供其状态。 如果您想要更改视某些条件的命令的状态，可以作为实例的创建命令<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>类，并在其构造函数，提供事件处理程序来执行命令和查询状态处理程序，以在该命令的状态发生更改时通知 Visual Studio。</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 您还可以实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>命令类或的一部分，您可以实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>如果你要为项目的一部分提供一个命令。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 两个接口和<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>类所有具有方法，以通知 Visual Studio 命令的状态的更改和其他方法，都执行此命令。</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
 当命令添加到命令服务中时，它只是一种命令链。 当实现该命令的状态通知和执行方法时，负责提供仅针对该特定命令并传递到其他命令的所有其他情况下，链中。 如果您不能将命令传递上 (通常通过返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>)，Visual Studio 可能会停止正常工作。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
## <a name="query-status-methods"></a>查询状态方法  
 如果您要实现任何一个<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法或<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>方法、 检查有无 command 设为此命令所属的 GUID 和命令的 ID。</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 请遵循这些指导：  
  
-   如果无法识别的 GUID，任何一种方法的实现必须返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   如果您的任何一种方法的实现识别 GUID，但不是实际实现了该命令，通过然后该方法应返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   如果任意一种方法实现可以识别的 GUID 和命令，则该方法应设置的每个命令的命令标志字段 (在`prgCmds`参数) 使用以下标志︰  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果支持该命令。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令不应可见。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令是否已切换，而且看起来已签入。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果启用了该命令。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果应隐藏该命令，如果它出现在快捷菜单上。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>如果该命令菜单控制器且未启用，但其下拉列表菜单列表不为空，且仍然可用。</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> （很少使用此标志。）  
  
-   如果在.vsct 文件中定义该命令`TextChanges`标志，设置以下参数︰  
  
    -   设置`rgwz`元素`pCmdText`对新的命令文本的参数。  
  
    -   设置`cwActual`元素`pCmdText`参数的命令字符串的大小。  
  
 此外确保当前上下文不是自动化函数，除非您的命令专门用于处理自动化功能。  
  
 若要显示支持特定的命令，返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。</xref:Microsoft.VisualStudio.VSConstants.S_OK> 对于所有其他命令，返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 在下面的示例中，查询状态方法首先确保上下文不是自动化函数，然后查找正确的命令集 GUID 和命令 id。 命令本身设置为启用和支持。 不支持任何其他命令。  
  
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
 Execute 方法的实现类似于查询状态方法的实现。 首先，请确保上下文不是自动化函数。 随后测试的 GUID 和命令 id。 如果 GUID 或命令无法识别 ID，返回<xref:Microsoft.VisualStudio.OLE.Interop.Constants>。</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 若要处理此命令，执行它，并返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>如果执行成功。</xref:Microsoft.VisualStudio.VSConstants.S_OK> 您的命令负责进行错误检测和通知;如果在执行失败，因此，返回错误代码。 下面的示例演示了应如何实现执行方法。  
  
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
 [Vspackage 如何添加用户界面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
