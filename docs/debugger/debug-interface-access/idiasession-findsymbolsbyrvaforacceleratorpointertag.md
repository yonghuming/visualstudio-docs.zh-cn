---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

将一个对应的标记值，此方法返回某个指定的相对虚拟地址的指定父快捷键存根函数包含符号的枚举。  
  
## 语法  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### 参数  
 `parent`  
 \[in\]对应于要搜索的快捷键存根功能的 `IDiaSymbol`。  
  
 `tagValue`  
 \[out\]指针标记值。  
  
 `rva`  
 \[in\]相对虚拟地址。  
  
 `ppResult`  
 \[out\]一个指向初始化结果的 `IDiaEnumSymbols` 接口指针的指针。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回错误值代码。  
  
## 备注  
 调用此方法仅在对应快捷键存根功能的 `IDiaSymbol` 接口。  
  
## 请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)