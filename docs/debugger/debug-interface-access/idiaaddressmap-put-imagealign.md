---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign 方法"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置图像对齐。  
  
## 语法  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### 参数  
 NewVal  
 \[in\] 可执行新图像对齐值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 图像 \(加载的可执行文件\) 对齐指定的内存边界。  此对齐受当前系统体系结构和编译和链接时选项的影响。  图像对齐始终在字节界。  下面的图像对齐值有效:1 个， 2 个， 4 个， 8 个， 16 个， 32 到 64 字节界。  
  
 当前图像对齐可以检索与 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) 方法的调用。  
  
> [!NOTE]
>  ，则此方法可调用时，图像已加载。  通常使用 `put_imageAlign` 方法，当图来移动或已更改后，并需要新的对齐方式。  
  
## 请参阅  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)