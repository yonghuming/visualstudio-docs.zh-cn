---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

返回符号的枚举内联帧的具有指定的内联函数名称相对应。  
  
## 语法  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### 参数  
 `name`  
 \[in\]要搜索的被内联方函数名。  
  
 `option`  
 \[out\]将使用的名称搜索选项搜索，则对应于 `name`的内联帧时。  有关更多信息，请参见 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)。  
  
 `ppResult`  
 \[out\]一个指向初始化结果的 `IDiaEnumSymbols` 接口指针的指针。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回错误值代码。  
  
## 备注  
 此功能只搜索inlinees在快捷键存根函数中。  它将忽略本机C\+\+程序记录。  
  
## 请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)