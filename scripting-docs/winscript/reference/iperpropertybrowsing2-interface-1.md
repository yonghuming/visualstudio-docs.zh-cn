---
title: "IPerPropertyBrowsing2 接口 1 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 接口 1
访问属性页中的信息提供的对象。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|`GetDisplayString`|返回指定的属性描述一个文本字符串。|  
|`MapPropertyToPage`|返回的 CLSID 的允许操作的指定属性的属性页。|  
|`GetPredefinedStrings`|返回字符串的计数的数组 (`LPOLESTR`指针) 列出允许指定的属性可以接受的值的说明。|  
|`SetPredefinedValue`|将属性的值设置为预定义的值由标记标识`dwCookie.`|  
  
## <a name="requirements"></a>要求  
 标头： dbgprop.h