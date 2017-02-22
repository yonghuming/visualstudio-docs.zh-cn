---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

retrieves 对应的字符串名称特定属性标识符。  
  
## 语法  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### 参数  
 `cpropid`  
 \[in\] 属性 ID 数。 `rgpropid`的。  
  
 `rgpropid`  
 \[in\] 数组属性 ID 获取名称 \(`PROPID` 在 WTypes.h 中定义为 `ULONG`\)。  
  
 `rglpwstrName`  
 \[in, out\] 属性名称指定的属性 ID。  必须预先指定数组保留属性名称的请求数，并且必须能够容纳至少 `cpropid``BSTR` 字符串。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 备注  
 必须释放返回的属性名称 \(通过调用 `SysFreeString` 函数\)，在不需要时。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)