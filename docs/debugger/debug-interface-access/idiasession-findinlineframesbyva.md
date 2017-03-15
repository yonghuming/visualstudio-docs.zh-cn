---
title: "IDiaSession::findInlineFramesByVA | Microsoft Docs"
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
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索允许客户端通过所有在指定的虚拟地址\(VA\)的内联帧重复的枚举。  
  
## 语法  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,  
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 参数  
 `parent`  
 \[in\] 表示父级的对象 `IDiaSymbol`。  
  
 `va`  
 \[in\] 指定地址为 VA。  
  
 `ppResult`  
 \[in\]一个包含帧列表检索的一 `IDiaEnumSymbols` 对象。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回错误值代码。  
  
## 请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)