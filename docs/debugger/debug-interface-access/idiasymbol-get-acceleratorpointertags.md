---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

返回对应于c. C\+\+ AMP快捷键存根函数的所有快捷键指针标记值。  
  
## 语法  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### 参数  
 `cnt`  
 \[in\]输出数组 `pPointerTags`的大小。  
  
 `pcnt`  
 \[in\]计数快捷键在C\+\+ AMP快捷键存根函数的指针标记。  
  
 `pPointerTags`  
 \[in\]一个 `DWORD` 填充快捷键指针标记的数组指针在C\+\+ AMP快捷键存根函数值。  
  
## 返回值  
 如果成功，则返回 `S_OK`，否则返回 `S_FALSE` 或者错误值代码。  
  
## 备注  
 此方法调用对应于c. C\+\+ AMP快捷键存根功能的 `IDiaSymbol` 接口。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)