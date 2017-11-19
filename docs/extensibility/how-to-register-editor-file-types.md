---
title: "如何： 注册编辑器文件类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9f2837dff6c5dd62c03da2ab340fca287a1da56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-register-editor-file-types"></a>如何： 注册编辑器文件类型
注册编辑器文件类型的最简单方法是通过使用作为的一部分提供的注册特性[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]托管包框架 (MPF) 类。 如果你要在本机实现你的包[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]，还可以编写注册表脚本注册你的编辑器和关联的扩展。  
  
## <a name="registration-using-mpf-classes"></a>使用 MPF 类注册  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>若要注册编辑器文件类型使用 MPF 类  
  
1.  提供<xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>编辑器中，你的 VSPackage 的类中的相应参数的类。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     其中"。示例"是，将为此编辑器，注册的扩展，"32"是其优先级别。  
  
     `projectGuid`是中定义的其他文件类型的 GUID <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>。 提供的其他文件类型，以便生成的文件不要生成过程的一部分。  
  
     `TemplateDir`表示包含所托管的基本编辑器示例附带的模板文件的文件夹。  
  
     `NameResourceID`BasicEditorUI 项目中，Resources.h 文件中定义并确定编辑器中的按"我编辑器"。  
  
2.  重写 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
     实现中<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法中，调用<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>方法并传入下面演示的作为你编辑器工厂的实例。  
  
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
  
     此步骤注册编辑器工厂和编辑器文件扩展名。  
  
3.  注销编辑器工厂。  
  
     释放 VSPackage 时，编辑器工厂会自动注销。 如果编辑器工厂对象实现<xref:System.IDisposable>接口，其`Dispose`后与已注销了工厂调用方法[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="registration-using-a-registry-script"></a>注册使用注册表脚本  
 在本机中注册编辑器工厂和文件类型[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]完成使用注册表脚本写入 windows 注册表中，如以下所示。  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>若要注册编辑器文件类型使用注册表脚本  
  
1.  在注册表脚本中，定义编辑器工厂和编辑器工厂 GUID 字符串中所示`GUID_BscEditorFactory`的以下注册表脚本部分。 此外，定义扩展和编辑器扩展的优先级：  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     在此示例中的编辑器文件扩展名标识为".rtf"并且其优先级为"50"。 Resource.h 文件 BscEdit 示例项目中定义的 GUID 字符串。  
  
2.  将 VSPackage 注册。  
  
3.  注册编辑器工厂。  
  
     在中注册的编辑器工厂<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>实现。  
  
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
  
     BscEdit 项目 Resource.h 文件中定义的 GUID 字符串。