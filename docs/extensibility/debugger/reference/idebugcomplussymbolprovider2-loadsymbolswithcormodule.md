---
title: "IDebugComPlusSymbolProvider2::LoadSymbolsWithCorModule | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider2::LoadSymbolsWithCorModule"
  - "LoadSymbolsWithCorModule"
ms.assetid: b6abf3a4-ce60-4e66-9637-82ce911148de
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider2::LoadSymbolsWithCorModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

加载调试符号给定 **ICorDebugModule** 对象。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT LoadSymbolsWithCorModule(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   BSTR      bstrModuleName,  
   BSTR      bstrSymSearchPath  
);  
```  
  
```c#  
int LoadSymbolsWithCorModule(  
   uint   ulAppDomainID,  
   Guid   guidModule,  
   ulong  baseAddress,  
   object pUnkMetadataImport,  
   object pUnkCorDebugModule,  
   string bstrModuleName,  
   string bstrSymSearchPath  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ulAppDomainID`  
 [in]应用程序域的标识符。  
  
 `guidModule`  
 [in]模块的唯一标识符。  
  
 `baseAddress`  
 [in]基本内存地址。  
  
 `pUnkMetadataImport`  
 [in]包含调试符号元数据的对象。  
  
 `pUnkCorDebugModule`  
 [in]实现对象 [ICorDebugModule 接口](ICorDebugModule%20Interface.xml)。  
  
 `bstrModuleName`  
 [in]模块的名称。  
  
 `bstrSymSearchPath`  
 [in]用于搜索符号文件的路径。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回 `S_OK`; 否则为返回错误代码。  
  
## <a name="example"></a>示例  
 下面的示例演示如何实现此方法对于 **CDebugSymbolProvider** 公开的对象 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) 接口。  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsWithCorModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* _pMetadata,  
    IUnknown* _pCorModule,  
    BSTR bstrModule,  
    BSTR bstrSearchPath)  
{  
    EMIT_TICK_COUNT("Entry -- Loading symbols for the following target:");  
    USES_CONVERSION;  
    EmitTickCount(W2A(bstrModule));  
  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    bool fSymbolsLoaded = false;  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(_pMetadata, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( _pMetadata, E_INVALIDARG );  
    IfFalseGo( _pCorModule, E_INVALIDARG );  
  
    IfFailGo( _pMetadata->QueryInterface( IID_IMetaDataImport,  
                                          (void**)&pMetadata) );  
  
    IfFailGo( _pCorModule->QueryInterface( IID_ICorDebugModule,  
                                           (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    //  
    //  We are now allowing modules to be created that do not have SymReaders.  
    //  It is likely there are a number of corner cases being ignored  
    //  that will require knowledge of the hr result below.  
    //  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
  
    HRESULT hrLoad = pmoduleNew->Create( idModule,  
                                         dwCurrentState,  
                                         pMetadata,  
                                         pCorModule,  
                                         bstrModule,  
                                         bstrSearchPath,  
                                         baseOffset );  
  
    if (hrLoad == S_OK)  
    {  
        fSymbolsLoaded = true;  
    }  
  
    // Remove the old module  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule( pmodule );  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    if (SUCCEEDED(hr) && !fSymbolsLoaded)  
    {  
        hr = hrLoad;  
    }  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
    EMIT_TICK_COUNT("Exit");  
    return hr;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)