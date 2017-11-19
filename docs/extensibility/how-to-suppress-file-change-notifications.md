---
title: "如何： 禁止显示文件更改通知 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88f7d2bf3a3351999175425366cf421c3b5ce0b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>如何： 禁止显示文件更改通知
更改表示文本缓冲区的物理文件后，对话框中显示并显示消息**你想要将更改保存到以下各项？** 这称为文件更改通知。 如果很多更改要为到该文件，但是，反复显示此对话框可以很快烦人。  
  
 以编程方式可禁止显示此对话框，使用以下过程。 通过执行此操作，你可以重新加载文件立即而无需提示用户每次保存所做的更改。  
  
### <a name="to-suppress-file-change-notification"></a>若要禁止显示文件更改通知  
  
1.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>方法来确定哪些文本缓冲区对象是与你打开的文件关联。  
  
2.  直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>内存中要忽略监视文件更改通过获取的对象<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>接口从<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>（文档数据） 对象，然后实现<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法替换`fIgnore`参数设置为`true`。  
  
3.  调用对象方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>接口，以便更新中内存<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>（例如何时将字段添加到你的组件） 的文件更改的对象。  
  
4.  使用更改更新磁盘上的文件，而无需考虑任何挂起的用户可能具有正在进行的编辑。  
  
     这种方式，当你直接<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>要恢复的文件监视对象更改通知，请在内存中的文本缓冲区反映生成，以及所有其他挂起的编辑的更改。 磁盘上的文件反映生成由你的最新代码，并且任何以前保存用户编辑的代码中的用户的更改。  
  
5.  调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>方法通知<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>对象继续监视文件更改通知，通过设置`fIgnore`参数`false`。  
  
6.  如果你打算对该文件，如下所示的源代码管理 (SCC)，这种情况进行一些更改，你必须告知全局文件更改服务以暂时挂起文件更改通知。  
  
     例如，如果您重写文件，然后更改时间戳，你必须挂起文件更改通知，如在重写和 timestample 操作每个计数为单独的文件更改事件。 若要启用应改为调用的全局文件更改通知<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>方法。  
  
## <a name="example"></a>示例  
 下面演示如何禁止显示文件更改通知。  
  
```cpp  
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
  
## <a name="robust-programming"></a>可靠编程  
 如果你的用例涉及多项更改的文件，如下所示的 SCC，则这种情况然后很重要警报文档数据恢复的文件更改监视之前恢复全局文件更改通知。