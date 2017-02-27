---
title: "IDiaSymbol::get_hasManagedCode | Microsoft Docs"
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
  - "IDiaSymbol::get_hasManagedCode 方法"
ms.assetid: e40f82f5-88fe-4a9b-b594-3605f42773ec
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_hasManagedCode
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指示模块是否的标志包含托管代码。  
  
## 语法  
  
```cpp#  
HRESULT get_hasManagedCode(  
   BOOL *pFlag  
);  
```  
  
#### 参数  
 `pFlag`  
 \[out\] ，如果模块包含托管代码，则返回; `TRUE` 否则，返回 `FALSE`，代码都是非托管代码。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
 此属性从 `SymTagCompilandDetails` 符号类型可用 \(请参见 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)\)。  
  
## 要求  
  
|要求|说明|  
|--------|--------|  
|标题:|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)