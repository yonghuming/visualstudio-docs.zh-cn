---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile 方法"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

通过编译和名称检索源文件。  
  
## 语法  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### 参数  
 `pCompiland`  
 \[in\] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 对象表示编译，该编译被用作上下文以供搜索。  设置此参数至 `NULL` 以找到在所有的 compilands 内的源文件。  
  
 `name`  
 \[in\] 指定要检索的源文件的名称。  设置此参数至取回所有源文件的 `NULL`。  
  
 `option`  
 \[in\] 指定用于名称搜索的比较选项。  [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md) 来自枚举中值可以单独使用又可与其他类组合使用。  
  
 `ppResult`  
 \[out\] 返回包含检索的源文件的列表的 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) 对象。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回错误值代码。  
  
## 示例  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## 请参阅  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)