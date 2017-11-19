---
title: "单个和多选项卡的视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c90f7cec454cc6562e2cd20e2da64cfe86e243f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="single-and-multi-tab-views"></a>单个和多选项卡的视图
编辑器可以创建不同类型的视图。 另一种是窗体设计器，一个示例是一个代码编辑器窗口。  
  
 多选项卡式视图是具有多个选项卡的视图。 例如，HTML 编辑器底部有两个选项卡：**设计**和**源**，每个逻辑视图。 设计视图显示呈现的网页上，而另一个显示包含 web 页的 HTML。  
  
## <a name="accessing-physical-views"></a>访问物理视图  
 物理视图托管文档视图对象，每个元素表示的缓冲区，如代码或表单中的数据的视图。 相应地，每个文档视图对象，并且在物理视图 （由内容称为物理查看字符串标识），通常单个逻辑视图。  
  
 不过，在某些情况下，物理视图可具有两个或多个逻辑视图。 一些示例包括一个编辑器，具有与并排显示视图拆分窗口或窗体设计器具有 GUI/设计视图和代码隐藏的窗体视图。  
  
 若要启用你的编辑器，若要访问所有可用的物理视图，必须创建每种类型的编辑器工厂可以创建的文档视图对象的唯一物理视图字符串。 例如，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]编辑器工厂可创建文档的代码窗口和窗体设计器窗口的视图对象。  
  
## <a name="creating-multi-tabbed-views"></a>创建多选项卡式视图  
 尽管文档视图对象必须与通过唯一物理视图字符串物理视图相关联，你可以将物理视图，则允许的数据查看不同的方式中的多个选项卡。 在此多个选项卡配置中，所有选项卡具有相同的物理查看字符串，与关联，但每个选项卡提供不同的逻辑视图 GUID。  
  
 若要为编辑器创建多个选项卡的视图，实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>接口，然后将关联不同的逻辑视图 GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) 创建与每个选项卡。  
  
 Visual Studio HTML 编辑器是与多选项卡视图编辑器的示例。 它具有**设计**和**源**选项卡。 若要启用此功能，不同的逻辑视图为每个选项卡上，与关联`LOGICALVIEWID_TextView`为**设计**选项卡和`LOGICALVIEWID_Code`为**源**选项卡。  
  
 通过指定适当的逻辑视图，VSPackage 可以访问的视图，对应于某种特定用途，如设计窗体、 编辑代码，或调试代码。 但是，一窗口必须由字符串为空，并且此值必须对应于主逻辑视图 (`LOGVIEWID_Primary`)。  
  
 下表列出可用的逻辑视图值和其使用。  
  
|LOGVIEWID GUID|建议的使用|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|编辑器工厂的默认/主视图。<br /><br /> 所有编辑器工厂必须都支持此值。 此视图必须使用 NULL 字符串作为其物理查看字符串。 至少一个逻辑视图必须设置为此值。|  
|`LOGVIEWID_Debugging`|调试视图。 通常情况下，`LOGVIEWID_Debugging`映射到同一个视图作为`LOGVIEWID_Code`。|  
|`LOGVIEWID_Code`|由启动视图**查看代码**命令。|  
|`LOGVIEWID_Designer`|由启动视图**查看表单**命令。|  
|`LOGVIEWID_TextView`|文本编辑器视图。 这是返回的视图<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>，你可以访问从<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|`LOGVIEWID_UserChooseView`|提示用户选择要使用哪个视图。|  
|`LOGVIEWID_ProjectSpecificEditor`|通过传递**打开**到对话框<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 当用户选择"（项目默认编辑器）"条目。|  
  
 尽管逻辑视图 Guid 是可扩展的你可以使用仅在你的 VSPackage 中定义的逻辑视图 Guid。  
  
 在关机时，Visual Studio 将保留编辑器工厂和与文档窗口中，以便它可以用于重新打开解决方案时，重新打开文档窗口关联的物理视图字符串的 GUID。 关闭解决方案时所打开的 windows 解决方案 (.suo) 文件中保留。 这些值对应于`VSFPROPID_guidEditorType`和`VSFPROPID_pszPhysicalView`传入值`propid`中的参数<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法。  
  
## <a name="example"></a>示例  
 此代码段演示了如何<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>对象用于访问实现视图`IVsCodeWindow`。 在这种情况下，<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>服务用于调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>和请求`LOGVIEWID_TextView`，其中包含一个指向窗口框架。 通过调用获取指向文档视图对象的指针<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>和指定的值`VSFPROPID_DocView`。 从文档视图对象，`QueryInterface`为调用`IVsCodeWindow`。 应当在这种情况下是返回的文本编辑器，并因此文档视图对象返回在<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>方法是一个代码窗口。  
  
```cpp  
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
  
## <a name="see-also"></a>另请参阅  
 [支持多个文档视图](../extensibility/supporting-multiple-document-views.md)   
 [如何： 附加文档数据的视图](../extensibility/how-to-attach-views-to-document-data.md)   
 [创建自定义编辑器和设计器](../extensibility/creating-custom-editors-and-designers.md)