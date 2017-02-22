---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry 枚举"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在地址图描述项。  
  
## 语法  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elements  
 `rva`  
 在图像 A. 的相对 \(RVA\)虚拟地址。  
  
 `rvaTo`  
 该相对虚拟地址 `rva` 映射到图像 B。  
  
## 备注  
 地址图提供从一个图像格式\) 的转换到另一 \(b\)。  数组 `rva` 排序的 `DiaAddressMapEntry` framework 定义了一个地址图。  
  
 若要将地址， `addrA`，在图像为地址， `addrB`，在图像 B，执行以下步骤:  
  
1.  搜索映射项， `e`，和最大的 `rva` 小于或等于 `addrA`。  
  
2.  设置 `delta = addrA – e.rva`。  
  
3.  设置 `addrB = e.rvaTo + delta`。  
  
 数组 `DiaAddressMapEntry` 结构传递给 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 方法。  
  
## 要求  
 标题:dia2.h  
  
## 请参阅  
 [枚举和结构](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)