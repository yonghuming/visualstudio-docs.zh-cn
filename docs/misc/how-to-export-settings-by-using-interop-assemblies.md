---
title: "如何：使用互操作程序集导出设置 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE 设置, 使用互操作程序集导出"
  - "用户设置 [Visual Studio SDK], 使用互操作程序集导出"
  - "IDE, 使用互操作程序集导出设置"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 如何：使用互操作程序集导出设置
VSPackage 可以从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 中导出设置。 IDE 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口的 VSPackage 的实现。 如果包还提供了 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 接口，则 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 接口用于确定保存 VSPackage 的配置的方式。  
  
> [!NOTE]
>  托管的包框架 \(MPF\) 提供了一套托管类来帮助创建 Visual Studio 扩展。 若要使用 MPF 执行此任务，请参阅[导出设置](../misc/exporting-settings.md)。  
  
### 若要在 VSPackage 上实现设置导出  
  
1.  实现对 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置机制的基本支持。  
  
    -   通过定义一个或多个自定义设置点，将 VSPackage 注册为支持该设置机制。  
  
         有关更多信息，请参见[用户设置的的支持](../extensibility/internals/support-for-user-settings.md)。  
  
    -   声明 VSPackage 实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>。 如果需要，VSPackage 还可以实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 接口。 例如:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   确保 VSPackage 对 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 方法的实现在使用 `IID_IVsUserSettings` 调用时提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口。  
  
         （可选）`QueryInterface` 可以在使用 `IID_IVsUserSettingsQuery` 接口调用时提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 接口。  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  （可选）警告需要的 IDE 导出特定设置。  
  
     VSPackage 可以选择有条件地保存自定义设置点状态定义的设置。 例如，只有当用户明确指示要保存设置时才保存。  
  
     在这种情况下，必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> 接口。  
  
     如果 VSPackage 未实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>，则其所有状态信息在设置导出过程中保存。  
  
     VSPackage 可以支持多个自定义设置点（设置类别）。 实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> 方法必须检查所提供的自定义设置点的 GUID 或设置类别参数，以确定是否必须保存一组特定的设置。  
  
     在以下示例中，VSPackage 总是要求保存其命令栏状态，但只请求在已设置标志的情况下保存其键绑定状态。  
  
3.  将设置数据写入到设置文件。  
  
     若要支持导出设置，VSPackage 必须始终实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 方法。  
  
     实现必须处理由 IDE、该自定义设置点类别的 GUID 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 接口传递的参数。  
  
    1.  VSPackage 可以支持多个自定义设置点（设置类别）。 在以下示例中，与保持键绑定状态相反，<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 方法调用不同的实现以保持命令栏状态。  
  
    2.  VSPackage 必须使用所提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 接口以将数据保存到设置文件。  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         提供给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 接口的 `pszSettingName` 参数的值必须唯一地标识每个保存在设置类别中的数据元素。  
  
        > [!NOTE]
        >  在自定义设置点中名称必须为唯一，因为 IDE 使用其 GUID 和 `pszSettingName` 的值来标识每个保存的设置。 如果使用 `pszSettingName` 的相同值来调用超过一个 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 方法，则设置文件中的原始值会被覆盖。  
  
         设置文件支持随机数据访问。 因此，读取和写入设置操作的顺序并不重要。  
  
         在以下示例中的导出和导入命令栏状态（`ExportSettings_CommandBa`r 和 `ImportSettings_CommandBar`）的实现中演示了这一点。  
  
         如果该实现可以将数据映射到四个受支持的格式之一，对于可以写入多少和哪些类型的数据并没有限制。  
  
        > [!NOTE]
        >  除了显式写入和对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 实现透明的数据以外，设置 API 还保存了 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本信息。 保存的设置可与在设置导入过程中生成它们的 IDE 版本进行比较。  
  
## 示例  
 以下示例演示如何使用导入和导出设置数据。  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## 请参阅  
 [用户设置的的支持](../extensibility/internals/support-for-user-settings.md)   
 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)   
 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [如何：使用互操作程序集导入设置](../misc/how-to-use-interop-assemblies-to-import-settings.md)