---
title: "IDiaSymbol::get_age | Microsoft Docs"
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
  - "IDiaSymbol::get_age 方法"
ms.assetid: 60d05654-e832-4a2e-a4a7-fe9922c459fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_age
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索 .pdb 文件的年龄值。  
  
## 语法  
  
```cpp#  
HRESULT get_age (   
   DWORD* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回 .pdb 文件的年龄值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
 年龄不一定对应于任何已知的时间值;通常用于确定 .pdb 文件是否不同步的与相应的 .exe 文件。  
  
## 要求  
  
|要求|说明|  
|--------|--------|  
|标题:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)