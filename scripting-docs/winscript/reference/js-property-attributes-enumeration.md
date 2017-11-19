---
title: "JS_PROPERTY_ATTRIBUTES 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed034ef6fc134838058b75534f1b5c17c1ec2e3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="jspropertyattributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES 枚举
指示属性的特性。  
  
## <a name="syntax"></a>语法  
  
```  
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>成员  
  
|名称|描述|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|该属性具有任何属性。|  
|`JS_PROPERTY_HAS_CHILDREN`|该属性具有子级。|  
|`JS_PROPERTY_FAKE`|该属性表示假节点，如"[方法]"。|  
|`JS_PROPERTY_METHOD`|属性是一种方法。|  
|`JS_PROPERTY_READONLY`|该属性是只读的。|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|属性是指向本机 WinRT 对象的指针。|  
  
## <a name="requirements"></a>要求  
 **标头：** jscript9diag.h  
  
## <a name="see-also"></a>另请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)