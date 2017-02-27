---
title: "IDiaPropertyStorage::Enum | Microsoft Docs"
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
  - "IDiaPropertyStorage::Enum"
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

获取特性的枚举器中设置。  
  
## 语法  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### 参数  
 `ppenum`  
 \[out\] 返回 \(在 Microsoft.VisualStudio.OLE.Interop 命名空间\) 表示特性的枚举的 `IEnumSTATPROPSTG` 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则返回错误代码。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)