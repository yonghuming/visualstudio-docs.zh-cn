---
title: "如何: 注册编辑器文件类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK]，旧的注册文件类型"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 注册编辑器文件类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

注册编辑文件类型的最简单的方法是使用作为 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 托管包框架类的节中提供的注册属性 \(MPF\)。  如果实现在本机 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]的包，您还可以编写注册编辑器和关联的扩展的注册表脚本。  
  
## 使用 MPF 类注册  
  
#### 注册使用 MPF 类的编辑文件类型  
  
1.  提供 <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> 类具有相应的参数用于在 VSPackage 中类的编辑器。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     there “。sample”是注册此版本的扩展，并且， “32 " 是其优先级级别。  
  
     `projectGuid` 是杂项文件类型的 GUID，定义在 <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>。  提供杂项文件类型，因此，生成的文件不是生成过程的各部分。  
  
     `TemplateDir` 表示包含模板文件包含管理的基本编辑示例的文件夹。  
  
     `NameResourceID` 在 BasicEditorUI 项目的 Resources.h 文件中定义，并确定编辑为 “我的编辑”。  
  
2.  重写 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
     在 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法的实现中，调用 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 方法并通过编辑工厂的实例如下所示。  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     此步骤注册编辑器工厂和编辑文件扩展名。  
  
3.  注销编辑工厂。  
  
     ，在 VSPackage 中配置时，编辑工厂自动中注销。  如果编辑工厂对象实现 <xref:System.IDisposable> 接口，其 `Dispose` 方法调用，在工厂中注销与 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]之后。  
  
## 使用注册表脚本注册  
 注册表编辑器工厂和文件类型在本机 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 执行使用一个注册表脚本写入 windows 注册表，如的由以下。  
  
#### 注册使用注册表脚本的编辑文件类型  
  
1.  如下面的注册表脚本的 `GUID_BscEditorFactory` 节所示，在注册表脚本，请定义编辑器工厂和编辑 factory GUID 字符串。  另外，请定义扩展和编辑扩展的优先级别:  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     在此示例中的编辑文件扩展名标识 “.rtf”及其优先级 “50 "。  GUID 字符串。 BscEdit 示例项目的 Resource.h 文件中定义的。  
  
2.  注册 VSPackage。  
  
3.  注册编辑器工厂。  
  
     编辑工厂。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 实现注册。  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID 字符串。 BscEdit 项目的 Resource.h 文件中定义的。