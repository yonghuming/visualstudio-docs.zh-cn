---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "IDiaAddressMap::set_imageHeaders 方法"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

设置图像标题启用相对虚拟地址转换。  
  
## 语法  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### 参数  
 cbData  
 \[in\] 字节数头数据。  必须是 `n*sizeof(IMAGE_SECTION_HEADER)``n` 是部分报头数在可执行文件的位置。  
  
 数据 \[\]  
 \[in\] 数组为图像标题将使用的 `IMAGE_SECTION_HEADER` 结构。  
  
 originalHeaders  
 \[in\] 设置为 `FALSE` ，如果图像标题是从新图像， `TRUE` ，如果是在升级之前反映原始图像。  通常，这仅设置为 `TRUE` 与的组合调用 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 方法。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 `IMAGE_SECTION_HEADER` 结构在 Winnt.h 中声明并表示图像部分报头格式可执行文件。  
  
 相对虚拟地址 \(rva\) 计算取决于 `IMAGE_SECTION_HEADER` 值。  通常， DIA 从程序数据库 \(.pdb\) 文件中检索这些。  如果这些值丢失， DIA 无法计算相对虚拟地址，然后 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 方法返回 `FALSE`。  客户端必须然后调用 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) 方法在提供从图像中缺少图像标头之后启用相对虚拟地址 \(rva\) 计算。  
  
## 请参阅  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)