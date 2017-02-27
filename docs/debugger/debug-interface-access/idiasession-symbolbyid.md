---
title: "IDiaSession::symbolById | Microsoft Docs"
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
  - "IDiaSession::symbolById 方法"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由其唯一标识符检索符号。  
  
## 语法  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### 参数  
 `id`  
 \[in\] 唯一标识符。  
  
 `ppSymbol`  
 \[out\] 返回表示检索的符号的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 该指定的标识符是 DIA SDK 在内部用于的唯一值使所有符号唯一。  
  
 此方法可用于，例如，检索表示另一个符号的类型符号 \(参见示例\)。  
  
## 示例  
 此示例检索表示另一个符号的类型 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 。  此示例在会话中演示如何使用 `symbolById` 方法。  一种更简单的方法是调用 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) 方法直接检索该类型符号。  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## 请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)