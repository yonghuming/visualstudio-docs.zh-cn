---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap 方法"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

提供一个地址图表支持图像格式的转换。  
  
## 语法  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### 参数  
 `cbData`  
 \[in\] 元素数。 `data` 参数的。  
  
 `data[]`  
 \[in\] 数组定义转换映射的 [DiaAddressMapEntry 结构](../../debugger/debug-interface-access/diaaddressmapentry.md) 结构。  
  
 `imagetoSymbols`  
 \[in\] `TRUE` ，如果 `data` 参数定义从新图像格式的映射到原始格式 \(如所描述的调试符号\)。  `FALSE` ，如果 `data` 是映射到从原始布局采用的新图像格式。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 通常， DIA 从程序数据库 \(.pdb\) 文件中检索地址转换映射。  如果这些值丢失， [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 方法两次，一次调用与 `imagetoSymbols` 参数设置为 `TRUE` 一次使用 `imagetoSymbols` 参数设置为 `FALSE`。  ，除非提供，地址图表将无法启用使用 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md) 方法两次转换映射。  
  
## 请参阅  
 [DiaAddressMapEntry 结构](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)