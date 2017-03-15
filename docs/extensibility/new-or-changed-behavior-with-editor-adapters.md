---
title: "新的或更改行为与编辑器适配器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的适配器行为"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 新的或更改行为与编辑器适配器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果要更新针对早期版本的 Visual Studio 核心编辑器中，编写的代码，并且您打算使用的编辑器适配器 （或填充程序），而不是使用新的 API，应注意以下与以前的核心编辑器编辑器适配器的行为差异。  
  
## 功能  
  
#### 使用 SetSite\(\)  
 必须调用 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> 时共同创建文本缓冲区中，文本视图和代码窗口，然后才能执行对它们的任何其他操作。 但是，这不是有必要，如果您使用 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 来创建它们，因为此服务的 create （） 方法自身调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>。  
  
#### 在您自己的内容中承载 IVsCodeWindow 和 IVsTextView  
 您可以托管同时 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 内容使用 Win32 模式或 WPF 模式中。 但是，您应记住有两种模式中的一些差异。  
  
##### 使用 Win32 和 WPF 版本 IVsCodeWindow  
 代码编辑器窗口派生自 <xref:Microsoft.VisualStudio.Shell.WindowPane>, ，用来实现较旧的 Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 接口以及新的 WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> 接口。 您可以使用 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> 方法来创建基于 HWND 的宿主环境中，或 <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> 方法来创建 WPF 宿主环境。 基础编辑器会始终使用 WPF 中，但您可以创建适合自己的托管要求，如果您要嵌入此窗口窗格直接插入您自己的内容的窗口窗格中的类型。  
  
##### 使用 Win32 和 WPF 版本 IVsTextView  
 您可以设置 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 为 Win32 模式或 WPF 模式。  
  
 当编辑器工厂创建的文本视图中，默认情况下位于 HWND，和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> 返回 HWND。 不应使用此模式下将嵌入在 WPF 控件内部的编辑器。  
  
 若要设置为 WPF 模式的文本视图，必须调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> 并传入 <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> 如标记中的初始化之一 `InitView` 参数。 你可以获取 <xref:System.Windows.FrameworkElement> 通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>。  
  
 WPF 模式与 Win32 模式下，两种方式不同。 首先，可以在 WPF 的上下文中承载文本视图。 您可以访问 WPF 窗格中，通过强制转换 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> 并调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>。 第二个， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> 仍的返回使用，但此 HWND HWND，而是为了检查其位置和焦点设置在其上。 不必须使用此 HWND 来响应 WM\_PAINT 消息，因为它不会影响编辑器如何绘制窗口中。 此 HWND 只是为了便于通过适配器的过渡到新的编辑器代码。 强烈建议您不应使用 `VIF_NO_HWND_SUPPORT` 如果您的组件要求 HWND 工作，由于在从返回的 HWND 限制 `GetWindowHandle` 而在此模式下。  
  
#### 将数组作为参数传递在本机代码中  
 有许多旧式编辑器 API 的方法具有参数，其中包括数组和其计数。 示例包括︰  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 如果要在本机代码中调用这些方法，则必须一次传递中只有一个元素。 如果您通过在多个元素中，调用将被拒绝，由于与主互操作实现的问题。  
  
 问题是更复杂的方法，如 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>。 每次调用此方法时，它会清除前面已忽略的标记类型的列表，因此不可能只是为了与三种不同的标记类型三次调用此方法。 唯一的补救措施是仅在托管代码中调用此方法。  
  
#### 线程处理  
 您应始终从 UI 线程上调用缓冲区适配器。 缓冲区适配器是一个托管的对象，这意味着它调用从托管代码会绕过 COM 封送处理，并且您的呼叫将不会自动封送到 UI 线程。  如果您正在从后台线程调用缓冲区适配器，则必须使用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 或类似方法。  
  
#### LockBuffer 方法  
 所有 LockBuffer\(\) 方法已都弃用。 示例包括︰  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### 提交的事件  
 提交不支持这些事件。 调用的方法，建议为这些事件会导致该方法返回了失败代码。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> 不再激发 commit （） 上。 而是它们激发上文本的每项更改。  
  
#### 文本标记  
 必须调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> 上 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> 对象时删除它们。 在以前版本，您只需发布标记。  
  
#### 行号  
 上的方法很多 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, 、 行号对应于基础缓冲区行号、 不限行号以大纲方式显示和自动换行，像 Visual Studio 2008 中的因素。  
  
 受影响的方法如下 （列表并不详尽）︰  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### 大纲显示  
 客户端的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 将看到仅使用已添加这些大纲区域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>。 他们将看不到临时区域，因为它们没有添加通过编辑器适配器。 同样，这些客户端不会看到大纲区域添加新的编辑器代码，而不是编辑器适配器使用的语言 （包括 C\# 和 c \+ \+）。  
  
#### 行的高度  
 在新的编辑器中，文本行可具有不同的高度，具体取决于字号和可能的行可能会移动相对于其他行的行的转换。 如由方法返回的行高度 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> 应用没有行转换中使用的默认字体大小的行的高度。 此高度可能或可能不会反映实际视图中的行的高度。  
  
#### 事件和撤消  
 在新的编辑器中，视图将继续执行操作，例如呈现和连续引发事件，即使撤消群集处于打开状态。 此行为是不同于未执行撤消群集的这些操作结束后之前, 的旧视图。  
  
#### IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> 方法将失败，如果您没有实现的类以传递 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> 或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>。 不再支持自定义 Win32 所有者描述弹出窗口。  
  
#### 智能标记  
 没有适配器支持的智能标记，创建 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, ，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, ，和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> 接口。  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> 未实现。  
  
## 未实现的方法  
 某些方法尚未实现对文本缓冲区适配器、 文本视图适配器和文本层适配器。  
  
|接口|未实现|  
|--------|---------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` 未实现。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> 在但会将其忽略大纲显示用户界面的适配器实现。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> 在但会将其忽略大纲显示用户界面的适配器实现。|