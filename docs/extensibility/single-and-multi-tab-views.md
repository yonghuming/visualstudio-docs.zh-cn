---
title: "单个和多选项卡上的视图 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，自定义的单个和多选项卡上的视图"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# 单个和多选项卡上的视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可编辑视图创建具有不同的类型。  一个示例是代码编辑器窗口，还有窗体设计器。  
  
 一个多个选项卡式视图是有多个选项卡的视图。  例如， HTML 编辑器有两个选项在底部: **设计** 和 **源**，每个逻辑视图。  设计 " 视图中显示一个呈现的网页，，而其他显示包含该网页的 HTML。  
  
## 访问的物理视图  
 物理视图宿主文档视图对象，该对象表示数据检查缓冲区的每一，如代码或窗体。  因此，每个文档视图对象都有一个物理视图 \(由称为的物理视图字符串内容\) 以及通常一个逻辑视图。  
  
 有时，不过，，一个物理视图可以具有两个或多个逻辑视图。  某些示例是具有拆分窗口有并行视图的编辑，或者有一个 GUI\/design 视图和一个代码在其后的窗体视图的窗体设计器。  
  
 若要启用编辑器为可用物理视图的访问，都必须为每种类型创建单个物理视图字符串文档编辑器工厂可以创建的视图对象。  例如， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 编辑工厂可以创建文档代码和 windows 窗体设计器窗口的视图对象。  
  
## 创建多个选项卡式视图  
 尽管必须与文档视图对象的一个物理视图通过单个物理视图字符串时，可以放置在一个物理视图中的多个选项启用数据检查以不同的方式。  此多选项卡式配置，所有选项与同一物理视图字符串，但是，为每个选项不同的逻辑视图 GUID。  
  
 若要创建编辑器创建一个多选项卡式视图，请实现接口 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> 然后将不同的逻辑视图、 GUID \(<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>\) 与您创建的每个选项。  
  
 Visual Studio HTML 编辑器是一个编辑器的示例有多选项视图。  它具有 **设计** 和 **源** 选项。  若要实现此功能，一个不同的逻辑视图与每个选项卡、 `LOGICALVIEWID_TextView`**设计** 可选的和 `LOGICALVIEWID_Code`**源** 可选的。  
  
 通过指定一个相应的逻辑视图， VSPackage 可以访问与特殊的目的，例如设计窗体，编辑代码或调试代码的视图。  但是，必须用空字符串确定其中一个窗口，则必须对应于主逻辑视图 \(`LOGVIEWID_Primary`\)。  
  
 下表列出了可用的逻辑视图值及其用途。  
  
|LOGVIEWID GUID|推荐的使用|  
|--------------------|-----------|  
|`LOGVIEWID_Primary`|默认\/编辑器工厂的主视图。<br /><br /> 所有编辑器工厂都必须支持此值。  此视图必须使用空字符串作为其物理视图字符串。  必须至少设置逻辑视图。此值。|  
|`LOGVIEWID_Debugging`|调试视图。  通常， `LOGVIEWID_Debugging` 映射到视图和 `LOGVIEWID_Code`相同。|  
|`LOGVIEWID_Code`|**查看代码** 命令生成的视图。|  
|`LOGVIEWID_Designer`|**视图窗体** 命令生成的视图。|  
|`LOGVIEWID_TextView`|文本编辑器视图。  这是返回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>，可以访问 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>的视图。|  
|`LOGVIEWID_UserChooseView`|提示用户选择使用哪个视图。|  
|`LOGVIEWID_ProjectSpecificEditor`|通过 **打开。** 对话框<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 当用户选择 “\(项目的默认编辑器\)”项。|  
  
 虽然逻辑视图 GUID 是可扩展的，则在 VSPackage 只能使用逻辑视图中定义的 GUID。  
  
 在关闭， Visual Studio 保留编辑工厂的 GUID，并且实际视图字符串与文档窗口，使其可用于重新打开文档窗口，在重新打开解决方案时。  已打开的窗口，如果解决方案关闭时在解决方案 \(.suo\) 文件仍然存在。  这些值对应于在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 方法的 `propid` 参数传递的 `VSFPROPID_guidEditorType` 和 `VSFPROPID_pszPhysicalView` 值。  
  
## 示例  
 此代码段阐释如何使用 <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> 对象对该视图的实现 `IVsCodeWindow`的访问。  在这种情况下， <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> 服务用来调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 和请求 `LOGVIEWID_TextView`，获取一个指针到窗架。  对文档视图对象的指针通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 并指定 `VSFPROPID_DocView`的值获取。  从文档视图对象， `QueryInterface` 为 `IVsCodeWindow`调用。  预期在本例中是文本编辑器返回，并且，因此在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 方法返回的文档视图对象是代码窗口。  
  
```cpp#  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## 请参阅  
 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)   
 [如何︰ 附加视图文档数据](../extensibility/how-to-attach-views-to-document-data.md)   
 [创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)