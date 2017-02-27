---
title: "IDiaEnumFrameData::Clone | Microsoft Docs"
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
  - "IDiaEnumFrameData::Clone 方法"
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

创建包含枚举状态和枚举当前枚举数相同的枚举数。  
  
## 语法  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### 参数  
 ppenum  
 \[out\] 返回包含枚举数的副本 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) 对象。  框架数据没有重复，只有枚举数。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)