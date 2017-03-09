---
title: "如何：支持工具箱拖放功能 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "拖放, 在工具箱中受支持"
  - "工具箱 [Visual Studio SDK], 客户端"
  - "工具箱 [Visual Studio SDK], 拖放"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# 如何：支持工具箱拖放功能
> [!NOTE]
>  将自定义控件添加到工具箱建议的做法是，使用支持拖放功能的随 Visual Studio 10 SDK 提供的工具箱控件模板。 保留本主题仅为实现向后兼容性，以便用于现有控件。  
>   
>  有关使用模板创建工具箱控件的详细信息，请参阅 [如何：创建使用 Windows 窗体的工具箱控件](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) 和 [创建 WPF 工具箱控件](../extensibility/creating-a-wpf-toolbox-control.md)。  
  
 若要在文档视图中使用“工具箱”（如编辑器或设计器），则 Vspackage 必须实现拖放支持。  
  
 默认情况下，所有派生自 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 对象均将采用自动且透明的方式提供对使用“工具箱”控件的支持，因此，下面介绍的过程是不必要的。 这种基本功能可以通过创建设计器扩展。  
  
 有关详细信息，请参阅[Windows 窗体概述](../Topic/Windows%20Forms%20Overview.md)和[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)。  
  
### 实现基本拖放功能  
  
1.  通过在视图对象上实现 <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> 来提供拖放支持。 这将为视图提供 OLE 拖放功能并序列化控件。  
  
     有关实现拖放功能的详细信息，请参阅[拖放 \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole)。  
  
     “拖放项”可以是剪贴板项或设计器上拖放的控件。 有关“工具箱”[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]支持的标准剪贴板格式的信息，请参阅[扩展工具箱](../misc/extending-the-toolbox.md)。  
  
2.  在文档视图上提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 接口的基本实现。  
  
     当用户尝试将工具箱控件拖到视图时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 应查询该视图的 VSPackage，以查看是否实现了 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 接口。  
  
    1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>，以向拖放目标支持的“工具箱”格式返回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。 下面的示例将检查数据对象是否采用自定义剪贴板格式（`CF_CUSTOM_FORMAT`）以及该对象是否是 ActiveX 控件。  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         首次加载视图窗口，以及每次用户通过“自定义”“工具箱”对话框重置“工具箱”后激活视图窗口时，IDE 将检查此信息。 通常情况下，“工具箱”不会显示不受支持的“工具箱”项。  
  
         用户可以设置一个选项以在任何时候显示所有“工具箱”页面。 在这种情况下，环境不会针对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> 查询编辑器。  
  
    2.  <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> 实现（如上述的那个实现）成功处理拖放的组件后，视图对象必须通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A> 来通知 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 环境这一情况。  
  
     如果需要，VSPackage 可以通过扩展其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 实现来扩展它的拖放支持。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 实现可以支持通过选项而不是鼠标操作将“工具箱”项拖动到窗口。 也就是说，当用户双击“工具箱”项或单击后按 ENTER 键，可以拖动项。 具体方法为：  
  
    1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> 方法。  
  
         通过单击或通过按 ENTER 可选择由 IDE 调用的此方法。  
  
         该方法应将“工具箱”项插入到目标窗口中。  
  
    2.  如果你不希望通过选择支持该实现，该方法应返回 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>。  
  
         在下面的示例中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> 方法的实现会检查所选对象是否受支持，如果受支持则将其反序列化为代码：  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  执行以下步骤以确保为你的应用程序维持适当的关注：  
  
    1.  如果编辑器窗口实现两个不同的窗格，而不是两个不同的视图，则当在编辑器窗口中切换窗格激活时，调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> 方法。 只有你知道在你的窗口内何时发生了激活更改。  
  
    2.  若要正确激活窗口并确保命令路由已正确更新，则必须在组件上调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法。 当你将焦点设置到由涉及工具箱的拖放操作创建或修改的组件窗口（如编辑器）时，必须执行此操作。  
  
 VSPackage 可能需要介入拖动操作并通过 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> 接口修改拖放的项。  
  
 例如，不是将新的“工具箱”控件显式添加到“工具箱”中，而是当标准“工具箱”被拖放时，VSPackage 可能会将其截获，并替换为自定义实现。  
  
### 动态修改工具箱控件  
  
1.  实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> 方法。  
  
     每当选择或拖放“工具箱”项时，“工具箱”会查询拖放目标以查看它是否支持 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook> 接口，如果支持则将调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> 方法。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> 方法必须返回一个将使用的新的 <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> 而不是原始的 <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject>。  
  
     如果拖放目标不需要重写数据对象，则应返回其输入。  
  
 通过按 CTRL\+SHIFT\+V，VSPackage 可允许用户循环使用剪贴板的内容。  
  
### 支持剪贴板循环  
  
1.  使用以下内容为 `CMDIDPasteNextTBXCBItem` 命令实现处理程序：  
  
    -   对于基于互操作程序集的 Vspackage，使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
    -   对于基于托管包框架的 Vspackage，使用 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>。<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler> 接口。  
  
2.  在命令处理程序中，实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A> 方法，以确定是否具有要进行循环的任何剪贴板对象。  
  
    1.  如果在工具箱剪贴板上没有任何项，则环境会检查系统剪贴板，以查看它是否具有任何项。  
  
    2.  如果在系统剪贴板上具有项，但在工具箱剪贴板上没有项，则使用系统项填充剪贴板循环。  
  
    3.  若要在列表中选择下一项，则实现会调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A> 方法。  
  
    4.  若要返回到剪贴板循环的开头，则调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A> 方法。  
  
## 请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)   
 [如何：通过使用互操作程序集提供自定义工具箱项](../Topic/How%20to:%20Provide%20Custom%20Toolbox%20Items%20By%20Using%20Interop%20Assemblies.md)   
 [高级工具箱控件开发](/visual-cpp/misc/advanced-toolbox-control-development)   
 [注册工具箱支持功能](../misc/registering-toolbox-support-features.md)   
 [管理工具箱](/visual-cpp/misc/managing-the-toolbox)