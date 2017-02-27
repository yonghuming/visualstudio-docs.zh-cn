---
title: "IDiaInjectedSource | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaInjectedSource 接口"
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

访问插入了 DIA 数据源中存储的源代码。  
  
## 语法  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaInjectedSource`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaInjectedSource::get\_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|从源代码的字节 \(CRC\)检索计算的循环冗余检查。|  
|[IDiaInjectedSource::get\_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|检索字节数代码。|  
|[IDiaInjectedSource::get\_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|检索数据源的文件名。|  
|[IDiaInjectedSource::get\_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|检索该源编译的对象文件名称。|  
|[IDiaInjectedSource::get\_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|检索该名称将非文件源代码;即插入代码。|  
|[IDiaInjectedSource::get\_sourceCompression](../Topic/IDiaInjectedSource::get_sourceCompression.md)|检索使用的源压缩的指示符。|  
|[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|检索源代码字节。|  
  
## 备注  
 插入的源是在编译时插入的文本。  这并不意味着预处理器在 C\+\+ 的 `#include` 。  
  
## 调用方的说明  
 通过调用 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) 或 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md) 方法获取此接口。  用于获取 `IDiaInjectedSource` 接口的示例参见 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 接口。  
  
## 示例  
 此示例演示数据可从 `IDiaInjectedSource` 接口。  有关使用 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) 接口的替代方法，请参见。 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 接口的示例。  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)