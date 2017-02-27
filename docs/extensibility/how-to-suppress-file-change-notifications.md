---
title: "如何: 禁止显示文件更改通知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的禁止显示文件更改通知"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何: 禁止显示文件更改通知
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

当更改了表示文本缓冲区的物理文件，并显示消息 **是否希望保存对以下项的更改?**的对话框显示这称为 " 文件更改通知。  如果许多更改是到文件，但是，多种显示此的对话框可以迅速变得讨厌。  
  
 使用下面的过程中，可以通过编程方式取消显示此对话框。  这样一来，您便可以立即重新加载文件，而无需提示用户每次保存更改。  
  
### 禁止显示文件更改通知  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 方法确定文本缓冲区对象与打开文件。  
  
2.  处理在忽略监视文件更改的内存通过获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 接口从 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 的 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象 \(文档\) 数据对象，然后执行与设置为的 `fIgnore` 参数的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> 方法以 `true`。  
  
3.  调用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 接口的方法来更新的文件更改内存 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象 \(例如，当字段都将添加到该元素\) 时。  
  
4.  更新磁盘上的文件与更改不考虑任何挂起编辑用户可能具有正在进行。  
  
     ，这样，当您处理继续监视的 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象文件的更改通知时，内存中的文本缓冲区反映生成的更改，以及其他挂起的编辑。  磁盘上的文件以反映您和任何生成的最新代码由用户的以前保存的更改在用户编辑的代码中。  
  
5.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> 方法通过设置 `fIgnore` 参数通知到继续监视的 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 对象文件的更改通知。 `false`。  
  
6.  如果您计划对文件进行些许更改，在源代码管理 \(SCC\)，则必须调用全局文件更改服务暂停文件更改通知。  
  
     例如，因此，如果复盖文件然后将时间戳，您必须挂起文件更改通知，复盖，因为和 timestample 每个操作将计为一个单独的文件更改事件。  若要启用全局文件更改通知应调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> 方法。  
  
## 示例  
 下面的示例演示如何禁止显示文件更改通知。  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## 可靠编程  
 如果用例涉及到文件的多个更改，在 SCC，则务必在警告文档数据之前还原全局文件更改通知到的文件更改继续监视。