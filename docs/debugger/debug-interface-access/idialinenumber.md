---
title: "IDiaLineNumber | Microsoft Docs"
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
  - "IDiaLineNumber 接口"
ms.assetid: 1071f7d0-1f8c-4384-933f-c49c7eb930bd
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLineNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

描述用于处理从字节块图像文本对源文件行号的访问信息。  
  
## 语法  
  
```  
IDiaLineNumber : IUnknown  
```  
  
## 方法按 Vtable 顺序  
 下表显示 `IDiaLineNumber`方法。  
  
|方法|说明|  
|--------|--------|  
|[IDiaLineNumber::get\_compiland](../../debugger/debug-interface-access/idialinenumber-get-compiland.md)|检索对提供字节图像文本的编译符号。|  
|[IDiaLineNumber::get\_sourceFile](../Topic/IDiaLineNumber::get_sourceFile.md)|检索对源文件对象。|  
|[IDiaLineNumber::get\_lineNumber](../Topic/IDiaLineNumber::get_lineNumber.md)|检索源文件中的行号。|  
|[IDiaLineNumber::get\_lineNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-linenumberend.md)|检索语句或表达式的从一开始的源行号。|  
|[IDiaLineNumber::get\_columnNumber](../../debugger/debug-interface-access/idialinenumber-get-columnnumber.md)|检索该表达式或语句开始的列数。|  
|[IDiaLineNumber::get\_columnNumberEnd](../../debugger/debug-interface-access/idialinenumber-get-columnnumberend.md)|检索表达式或语句结束的列数。|  
|[IDiaLineNumber::get\_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)|检索块启动内存地址的部分部件。|  
|[IDiaLineNumber::get\_addressOffset](../../debugger/debug-interface-access/idialinenumber-get-addressoffset.md)|检索块启动内存地址的偏移量部件。|  
|[IDiaLineNumber::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idialinenumber-get-relativevirtualaddress.md)|检索块图像的相对 \(RVA\)虚拟地址。|  
|[IDiaLineNumber::get\_virtualAddress](../../debugger/debug-interface-access/idialinenumber-get-virtualaddress.md)|检索块的虚拟地址 \(VA\)。|  
|[IDiaLineNumber::get\_length](../Topic/IDiaLineNumber::get_length.md)|检索字节数在块中。|  
|[IDiaLineNumber::get\_sourceFileId](../../debugger/debug-interface-access/idialinenumber-get-sourcefileid.md)|检索提供此行的源文件的一个源文件标识符。|  
|[IDiaLineNumber::get\_statement](../Topic/IDiaLineNumber::get_statement.md)|检索指示的标志此行信息在程序源描述语句的开头。|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|检索提供此行的编译的唯一标识符。|  
  
## 备注  
  
## 调用方的说明  
 通过调用 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md) 或 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md) 方法获取此接口。  
  
## 示例  
 以下功能显示在函数的行号 \(表示 `pSymbol`\)。  
  
```cpp#  
void dumpFunctionLines( IDiaSymbol* pSymbol, IDiaSession* pSession )  
{  
    ULONGLONG length = 0;  
    DWORD     isect  = 0;  
    DWORD     offset = 0;  
  
    pSymbol->get_addressSection( &isect );  
    pSymbol->get_addressOffset( &offset );  
    pSymbol->get_length( &length );  
    if ( isect != 0 && length > 0 )  
    {  
        CComPtr< IDiaEnumLineNumbers > pLines;  
        if ( SUCCEEDED( pSession->findLinesByAddr(  
                                      isect,  
                                      offset,  
                                      static_cast<DWORD>( length ),  
                                      &pLines)  
                      )  
           )  
        {  
            CComPtr< IDiaLineNumber > pLine;  
            DWORD celt      = 0;  
            bool  firstLine = true;  
  
            while ( SUCCEEDED( pLines->Next( 1, &pLine, &celt ) ) &&  
                    celt == 1 )  
            {  
                DWORD offset;  
                DWORD seg;  
                DWORD linenum;  
                CComPtr< IDiaSymbol >     pComp;  
                CComPtr< IDiaSourceFile > pSrc;  
  
                pLine->get_compiland( &pComp );  
                pLine->get_sourceFile( &pSrc );  
                pLine->get_addressSection( &seg );  
                pLine->get_addressOffset( &offset );  
                pLine->get_lineNumber( &linenum );  
                printf( "\tline %d at 0x%x:0x%x\n", linenum, seg, offset );  
                pLine = NULL;  
                if ( firstLine )  
                {  
                    // sanity check  
                    CComPtr< IDiaEnumLineNumbers > pLinesByLineNum;  
                    if ( SUCCEEDED( pSession->findLinesByLinenum(  
                                                  pComp,  
                                                  pSrc,  
                                                  linenum,  
                                                  0,  
                                                  &pLinesByLineNum)  
                                  )  
                       )  
                    {  
                        CComPtr< IDiaLineNumber > pLine;  
                        DWORD celt;  
                        while ( SUCCEEDED( pLinesByLineNum->Next( 1, &pLine, &celt ) ) &&  
                                celt == 1 )  
                        {  
                            DWORD offset;  
                            DWORD seg;  
                            DWORD linenum;  
  
                            pLine->get_addressSection( &seg );  
                            pLine->get_addressOffset( &offset );  
                            pLine->get_lineNumber( &linenum );  
                            printf( "\t\tfound line %d at 0x%x:0x%x\n", linenum, seg, offset );  
                            pLine = NULL;  
                       }  
                    }  
                    firstLine = false;  
                }  
            }  
        }  
    }  
}  
```  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia80.dll  
  
## 请参阅  
 [接口（调试接口访问 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)   
 [IDiaEnumLineNumbers::Next](../../debugger/debug-interface-access/idiaenumlinenumbers-next.md)