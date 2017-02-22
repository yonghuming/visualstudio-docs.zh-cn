---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

reads 指定了从 set current 属性的属性。  
  
## 语法  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### 参数  
 `cpspec`  
 \[in\] 在 `rgpspec` 数组指定的计数属性。  如果为零，则方法不返回属性，但返回 `S_OK` 为成功代码。  
  
 `rgpspec`  
 \[in\] 要读取的属性数组。  属性可以指定由属性 ID 或由一个可选字符串名称。  按该数组中的任何特定顺序指定属性并不是必需的。  该数组可能包含重复的特性，从而重复属性值为简单属性返回。  非简单属性应返回 try 时访问被拒绝打开在第二次。  该数组可能包含属性 ID 和字符串 ID 杂注。  此数组必须具有属性值的至少 `cpspec` 数字。  
  
 `rgvar`  
 \[in, out\] 数组的每个属性的值 \(在 Microsoft.VisualStudio.OLE.Interop 命名空间\) 将填充的 `PROPVARIANT` 结构。  数组必须的大小至少 `cpspec` 元素。  调用方不需要初始化该数组中的值。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ; 如果未找到，则返回 `S_FALSE` 一个或多个特性。  否则返回错误代码。  
  
## 备注  
 如果未找到属性，在 `rgvar` 数组的对应项包含与 `VT_EMPTY`类型的 `VARIANT` 。  
  
## 请参阅  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)