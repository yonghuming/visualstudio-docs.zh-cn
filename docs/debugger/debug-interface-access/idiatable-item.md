---
title: "IDiaTable::Item | Microsoft Docs"
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
  - "IDiaTable::Item 方法"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在表中检索对指定的项。  
  
## 语法  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### 参数  
 `index`  
 \[in\] 表项的索引在范围为 0 到 \-1 `count`的，其中 `count` 用 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)方法返回。  
  
 `element`  
 \[out\] 返回表示指定的表项的 `IUnknown` 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 表表示对象的集合。  基于这些对象元素，参数可以转换为适当的接口。  例如，因此，如果表包含 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 对象，然后元素参数可以将强制转换为 `IDiaSegment` 接口。  
  
 它是调用 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 接口的 `QueryInterface` 方法适当的枚举器接口的和使用枚举数的特定方法的更常见的访问表内容。  有关示例参见 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 接口。  
  
## 请参阅  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)