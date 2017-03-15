---
title: "如何: 注册库与对象管理器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "库中，向对象管理器注册"
  - "IVsLibrary2 接口，与对象管理器注册库"
  - "IVsSimpleLibrary2 接口，与对象管理器注册库"
  - "IVsObjectManager2 接口，与对象管理器注册库"
  - "库、 符号浏览工具"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何: 注册库与对象管理器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

符号浏览工具，如 **类视图**， **对象浏览器**、 **调用浏览器** 和 **查找符号结果**，可以查看符号在项目或在外部组件。  符号包括命名空间、类、接口、方法和其他语言元素。  库跟踪这些符号并显示在并使用数据工具的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 对象管理器。  
  
 对象管理器记录所有可用的库。  每个库中提供符号前必须具有对象管理器注册为符号浏览工具。  
  
 通常，您注册库，在 VSPackage 加载。  但是，它可以在另一时间根据需要。  您注销库，在 VSPackage 关闭。  
  
 注册库，则使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> 方法。  在托管代码库，请使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。  
  
 要注销库，则使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 方法。  
  
 若要获取对对象管理器， <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 服务标识符为 `GetService` 方法。  
  
## 注册和注销具有对象管理器的库  
  
#### 注册具有对象管理器的库  
  
1.  创建库。  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  获取对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 类型的对象并调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。  
  
    ```vb#  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```c#  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### 注销程序具有对象管理器的库  
  
1.  获取对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 类型的对象并调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 方法。  
  
    ```vb#  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```c#  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## 请参阅  
 [遗留语言服务可扩展性](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [支持符号浏览工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何: 公开库对对象管理器提供的符号列表](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)