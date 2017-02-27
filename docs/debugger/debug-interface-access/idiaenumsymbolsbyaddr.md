---
title: "IDiaEnumSymbolsByAddr | Microsoft Docs"
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
  - "IDiaEnumSymbolsbyAddr 接口"
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaEnumSymbolsByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由多个符号在数据源中包含的地址枚举。  
  
## 语法  
  
```  
IDiaEnumSymbolsByAddr : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaEnumSymbolsByAddr`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|通过执行查找确定枚举数由部分和扭曲。|  
|[IDiaEnumSymbolsByAddr::symbolByRVA](../Topic/IDiaEnumSymbolsByAddr::symbolByRVA.md)|通过执行查找确定枚举数由相对虚拟地址 \(RVA\)。|  
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|通过执行查找确定枚举数由虚拟地址 \(VA\)。|  
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|由地址检索下符号按顺序。  所获取的元素数更新枚举数位置。|  
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|由地址检索以前的符号按顺序。  所获取的元素数更新枚举数位置。|  
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|复制该对象。|  
  
## 备注  
 此接口提供地址分组的符号。  例如若要使用类型分组符号时， `SymTagUDT` \(用户定义的类型\) 或 `SymTagBaseClass`，请使用 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 接口。  
  
## 调用方的说明  
 通过调用 [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md) 方法获取此接口。  
  
## 示例  
 此功能公开相对虚拟地址 \(rva\) 排序的所有符号名称和地址。  
  
```cpp#  
void ShowSymbolsByAddress(IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;  
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )  
    {  
        Fatal( "getSymbolsByAddr" );  
    }  
    CComPtr<IDiaSymbol> pSym;  
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )  
    {  
        Fatal( "symbolByAddr" );  
    }  
    DWORD rvaLast = 0;  
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )  
    {  
        pSym = 0;  
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )  
        {  
            Fatal( "symbolByAddr" );  
        }  
        printf( "Symbols in order\n" );  
        do  
        {   
            CDiaBSTR name;  
            if ( pSym->get_name( &name ) != S_OK )  
            {  
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );  
            }  
            else  
            {  
               printf( "\t0x%08X %ws\n", rvaLast, name );  
            }  
            pSym = 0;  
            celt = 0;  
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )  
            {  
                break;  
            }  
        } while ( celt == 1 );  
    }  
}  
```  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)