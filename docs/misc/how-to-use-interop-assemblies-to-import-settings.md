---
title: "如何：使用互操作程序集导入设置 | Microsoft Docs"
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
  - "IDE 设置, 使用互操作程序集进行导入"
  - "IDE, 使用互操作程序集导入设置"
  - "用户设置 [Visual Studio SDK], 使用互操作程序集进行导入"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 如何：使用互操作程序集导入设置
VSPackage 可以从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 中导入设置。 IDE 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口的 VSPackage 实现来确定如何检索 VSPackage 的配置。  
  
> [!NOTE]
>  托管的包框架 \(MPF\) 提供了一套托管类来帮助创建 Visual Studio 扩展。 若要使用 MPF 执行此任务，请参阅[导入设置](/visual-cpp/misc/importing-settings)。  
  
### 在 VSPackage 上实现设置导入  
  
1.  实现对 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 设置机制的基本支持。  
  
    -   通过定义一个或多个自定义设置点，将 VSPackage 注册为支持该设置机制。  
  
         有关详细信息，请参阅[用户设置的的支持](../extensibility/internals/support-for-user-settings.md)。  
  
    -   声明 VSPackage 实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口，例如：  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   确保 VSPackage 中 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 方法的实现在用 `IID_IVsUserSettings` 进行调用时提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口。 例如:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  检索设置信息。  
  
     若要支持检索设置信息，VSPackage 必须实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法。  
  
     若要读取数据，VSPackage 中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 接口的实现必须使用 IDE 传入的前两个参数：该自定义设置点类别的 GUID 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 接口。  
  
    1.  VSPackage 中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法的实现必须检查传入的类别 GUID，并为检索状态选择正确的机制。  
  
         在以下示例中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法调用与检索密钥绑定状态相反的不同实现来检索命令栏状态。  
  
    2.  VSPackage 必须使用所提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 接口以检索设置文件的数据。  
  
        > [!NOTE]
        >  如果设置信息作为 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本的一项功能而改变，则 VSPackage 中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法的实现必须在读取数据以检查 IDE 版本之前使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> 方法。  
  
         该接口提供从设置文件读取不同数据类型的方法。  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     设置文件支持随机数据访问，因此读取和写入设置操作的顺序并不重要。  
  
     以下示例在实现的导出和导入命令栏状态（`ExportSettings_CommandBa`r 和 `ImportSettings_CommandBar`）中演示了这一点。  
  
3.  验证检索到的数据。  
  
     设置信息包含在可以手动编辑的 XML 文件中。  
  
> [!IMPORTANT]
>  设置信息可能在磁盘上已损坏，也可能包含特定于版本的设置，因此无法用作恶意攻击的工具。 应验证 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 方法所返回每个数据项的有效性。  
  
-   若要验证对用于生成检索设置的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本的支持，请调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> 方法来检索版本。  
  
-   为使 IDE 通知用户某个导入的数据元素不进行验证，VSPackage 将调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> 方法。  
  
1.  应用设置信息。  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法的实现必须采用 IDE 传递给它的第三个参数的值。 支持的值是 <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags> 枚举的成员。 有关详细信息，请参阅<xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>。  
  
         在以下示例中，用于导入命令栏设置的实现 \(`ImportSettings_Commandbar`\) 使用此参数的值来确定应用设置时是要重写现有值还是要添加性地更新它们。  
  
    2.  在应用导入的设置时，必须实现透写式缓存方法。  
  
         必须在将设置应用到 IDE 的同时更新注册表或文件系统中的状态信息。 这能保证配置的连贯性性，并支持多实例 IDE 方案。  
  
2.  警报 IDE 如何处理设置导入。  
  
     使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法返回的 `pfRestartRequired` 参数来建议 IDE 是否需要重启以应用导入的设置。  
  
     如果 VSPackage 中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 方法的实现返回 `true`，则提示用户重启 IDE。  
  
## 示例  
 以下示例演示如何导入和导出设置数据。  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## 请参阅  
 [如何：使用互操作程序集导出设置](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [用户设置的的支持](../extensibility/internals/support-for-user-settings.md)   
 [扩展的用户设置和选项](../extensibility/extending-user-settings-and-options.md)   
 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)