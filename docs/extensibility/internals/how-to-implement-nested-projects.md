---
title: "如何: 实现嵌套的项目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "嵌套的项目中实现"
  - "项目 [Visual Studio SDK] 嵌套"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 实现嵌套的项目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在创建嵌套的项目类型时必须实现一些附加步骤。  父项对解决方案为其嵌套的一些相同的职责 \(子\) 项目。  父项目是一个容器项目与解决方案。  特别是，则必须由父项引发由解决方案和生成嵌套的项目层次结构的几个事件。  这些事件在下面介绍用于创建嵌套的项目过程。  
  
### 创建嵌套的项目  
  
1.  集成 \(IDE\)开发环境通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 接口填充父项目的项目文件和激活信息。  父项目即被创建并添加到解决方案。  
  
    > [!NOTE]
    >  此时，该值太早期父项目的过程可以创建嵌套项目，因为必须创建父项，则子项目中创建之前。  此顺序，父项目可以设置应用于子项如果需要，这些项可以从获取父的信息的子级项目。  ，如果它由客户端需要的打开如源代码管理 \(SCC\)和解决方案资源管理器中，此顺序如下。  
  
     父项目必须等待 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 方法由 IDE 调用，它可以创建其嵌套 \(子\) 之前项目或项目。  
  
2.  IDE 调用父项目的 `QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>的。  如果此调用成功， IDE 调用父的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 方法打开任何父项的嵌套项目。  
  
3.  父项调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> 方法通知侦听器嵌套用于创建新项目。  SCC，例如，侦听这些事件在生成解决方案和项目创建步骤的过程是否按顺序发生。  如果步骤失败中，解决方案可能无法正确迁移到源代码管理签入。  
  
4.  父项调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> 方法或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> 方法在其子项中的每一个。  
  
     通过 <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> 到 `AddVirtualProject` 方法指示应添加虚拟 \(嵌套\) 项添加到项窗口中，排除从生成，添加到源代码管理，依此类推。  `VSADDVPFLAGS` 可以控制该嵌套的项目的可见性和指示哪些功能与它。  
  
     如果您重新加载在父项目的项目文件中存储的项目 GUID 的以前现有子项，父项调用 `AddVirtualProjectEx`。  在 `AddVirtualProject` 和 `AddVirtualProjectEX` 之间的唯一区别是 `AddVirtualProjectEX` 有一些一个参数父项目指定每个实例 `guidProjectID` 为子项可以使 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> 正常工作。  
  
     如果没有可用的 GUID，例如，在添加新的嵌套项目时，解决方案创建一项，即添加到父时间。  是父项的职责在该项目 GUID 在其项目文件。  如果删除一个嵌套的项目，该项目 GUID 还可以被删除。  
  
5.  IDE 调用父项目的每个子项的 `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` 方法。  
  
     ，如果要嵌套项目，父项目必须实现 `IVsParentProject` 。  ，但是父项从不调用 `IVsParentProject` 的 `QueryInterface` ，即使它具有其下方的父项。  解决方案句柄 `IVsParentProject` 中调用和，则为; 如果实现，调用 `OpenChildren` 创建嵌套的项目。  `AddVirtualProjectEX` 从 `OpenChildren`总是调用。  在序列不应由父项调用它保留层次结构创建事件。  
  
6.  IDE 对子项的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 方法。  
  
7.  父项调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> 方法通知侦听器父的子元素项目中已创建。  
  
8.  ，在打开后， IDE 调用父项目的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> 方案的所有子项。  
  
     如果它已不存在，父项目通过调用 `CoCreateGuid`创建每个嵌套的项目的 GUID。  
  
    > [!NOTE]
    >  当 GUID，将创建时，`CoCreateGuid` 为调用的 COM API。  有关更多信息，请参见 `CoCreateGuid` 和 GUID MSDN Library。  
  
     父项。它在 IDE 中打开其下次要检索的项目文件存储此 GUID。  请参见步骤 4 有关更多信息与调用 `AddVirtualProjectEX` 相关检索子项的 `guidProjectID` 。  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 方法为您按照约定委托给了嵌套的项的父 ItemID 然后调用。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 检索嵌套项目要将节点的属性，则调用父时。  
  
     因为父元素和子元素项来实例化程序模型，您可以随时设置嵌套项的属性。  
  
    > [!NOTE]
    >  不仅可以从该嵌套的项目的上下文信息，但是，也可以询问父项是否具有该项目的任何上下文通过检查 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>。  在这样，您可以添加额外的动态帮助属性和特定菜单上的选项到单个嵌套的项目。  
  
10. 该层次结构中显示生成与调用的解决方案资源管理器为 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> 方法。  
  
     在解决方案资源管理器将该层次结构对环境 `GetNestedHierarchy` 生成显示的层次结构。  这样，解决方案知道该项存在并可用于生成管理由生成经理，也可以允许在项目文件置于源代码管理之下。  
  
11. 如果 Project1 的所有嵌套在创建项目后，控件通过回该解决方案，然后处理为 Project2 重复。  
  
     此扩展为创建嵌套的项来为具有子级的子项发生。  在这种情况下，因此，如果 BuildProject1，是 Project1 的子级，包含子项，它们将创建在 BuildProject1 之后且在 Project2 之前。  过程递归，并且该层次结构从上到下构建的。  
  
     当嵌套的项目关闭后，因为用户关闭解决方案或给定的项目，在 `IVsParentProject`， <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>的另一个方法，调用。  父项换行调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> 与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> 方法的方法通知侦听器添加到解决方案事件嵌套的项目已关闭。  
  
 以下主题处理一些其他概念可以考虑实现嵌套的项:  
  
 [有关卸载和重新加载嵌套项目的注意事项](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [嵌套项目的向导支持](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [实现处理嵌套项目命令](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [对嵌套项目的筛选 AddItem 对话框](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## 请参阅  
 [将项添加到添加新项对话框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)   
 [清单︰ 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [上下文参数](../../extensibility/internals/context-parameters.md)   
 [向导 \(。Vsz\) 文件](../../extensibility/internals/wizard-dot-vsz-file.md)