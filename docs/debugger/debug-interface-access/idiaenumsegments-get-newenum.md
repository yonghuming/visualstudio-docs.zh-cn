---
title: "IDiaEnumSegments::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumSegments::get__NewEnum 方法"
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索此枚举器的 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 版本。  
  
## 语法  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### 参数  
 pRetVal  
 \[out\] 返回表示此枚举器的 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 版本的 `IUnknown` 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)