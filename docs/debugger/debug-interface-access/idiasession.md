---
title: "IDiaSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession 接口"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

提供一个查询环境以调试符号。  
  
## 语法  
  
```  
IDiaSession : IUnknown  
```  
  
## 方法  
 下表显示了 `IDiaSession` 的方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|检索对应于此符号存储的符号可执行文件的加载地址。  这是传递给 `put_loadAddress` 方法的相同值。|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|。设置在此符号存储区中对应的符号的可执行文件的下载地址。 **Note:**  当您获取 `IDiaSession` 对象时和你开始使用该对象前，调用此方法是重要的。|  
|[IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)|在全局范围内索引引用。|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|检索在符号存储区中包含的所有表的枚举数。|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|在静态位置检索所有命名符号的枚举数。|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|检索与名称和符号类型匹配的一个指定的父标识符的所有子级。|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|检索一个指定的符号类型，该符号类型包含，或者是接近，一个指定的地址。|  
|[IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)|检索一个指定的符号类型，该符号类型包含，或者是接近，一个指定的相对虚拟地址\(RVA\)。|  
|[IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)|检索一个指定的符号类型，该符号类型包含，或者是接近，一个指定的虚拟地址\(VA\)。|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|检索包含符号指定的元数据标记的符号。|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|检查两个符号是否等效。|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|通过其唯一标识符检索符号。|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|检索一个指定的符号类型，该符号类型包含，或者是接近，一个指定的相对虚拟地址和偏移。|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|检索一个指定的符号类型，该符号类型包含，或者是接近，一个指定的虚拟地址和偏移。|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|通过编译和名称检索源文件。|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|通过源文件标识符检索源文件。|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|在指定的编译和源文件标识符中检索行号。|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|。在包含指定地址的指定编译中检索行。|  
|[IDiaSession::findLinesByRVA](../Topic/IDiaSession::findLinesByRVA.md)|在包含指定相对虚拟地址的指定编译中检索行。|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|在指定的地址范围内的行中，查找行号信息。|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|在指定的编译和源文件标识符和行号中检索行号。|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|检索源数据，该数据由属性提供程序或其他编译进程的组件放置到符号存储里。|  
|[IDiaSession::getEnumDebugStreams](../Topic/IDiaSession::getEnumDebugStreams.md)|检索调试数据流的一个枚举序列。|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|检索允许客户端通过所有在特定地址的内联帧重复的枚举。|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|检索允许客户端通过所有在指定的相对虚拟地址\(RVA\)的内联帧重复的枚举。|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|检索允许客户端通过所有在指定的虚拟地址\(VA\)的内联帧重复的枚举。|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|检索允许客户端通过所有功能行号信息重复内联，直接或间接，由指定的父符号的枚举。|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|检索允许客户端通过所有功能行号信息重复按指定的父符号内联，直接或间接，并在指定的地址范围内包含的枚举。|  
|[IDiaSession::findInlineeLinesByRVA](../Topic/IDiaSession::findInlineeLinesByRVA.md)|检索允许客户端通过所有功能行号信息重复按指定的父符号内联，直接或间接，并在指定的相对虚拟地址\(RVA\)中包含的枚举。|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|检索允许客户端通过所有功能行号信息重复按指定的父符号内联，直接或间接，并在指定的虚拟地址\(VA\)中包含的枚举。|  
|[IDiaSession::findInlineeLinesByLinenum](../Topic/IDiaSession::findInlineeLinesByLinenum.md)|检索允许客户端通过所有功能行号信息循环访问指定的源文件和行号内联，直接或间接，的枚举。|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|检索允许客户端通过所有内联函数行号信息重复与指定的名称的枚举。|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|返回符号的枚举变量的指定标记值对应于父快捷键存根功能。|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|将一个对应的标记值，此方法返回某个指定的相对虚拟地址的指定父快捷键存根函数包含符号的枚举。|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|返回符号的枚举内联帧的具有指定的内联函数名称相对应。|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|返回符号的枚举对应于指定的源位置的内联帧的。|  
  
## 备注  
 在创建 `IDiaSession` 对象之后调用[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) 方法给可访问的符号的所有虚拟地址 \(VA\) 属性是重要的，—传递给 `put_loadAddress` 方法的值必须是非零的。  加载地址来自任意加载的正在调试的可执行的程序。  例如，可以调用 Win32 函数 `GetModuleInformation` 以检索提供了句柄的可执行文件的加载地址。  
  
## 示例  
 此示例演示如何获取 `IDiaSession` 接口作为 DIA SDK 的泛型初始化的一部分。  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## 要求  
 头文件：Dia2.h  
  
 库：diaguids.lib  
  
 DLL：msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [查询 .Pdb 文件](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)