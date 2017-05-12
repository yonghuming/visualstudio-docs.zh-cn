---
title: "JS_PROPERTY_ATTRIBUTES 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JS_PROPERTY_ATTRIBUTES 枚举
指示属性的特性。  
  
## 语法  
  
```  
enum JS_PROPERTY_ATTRIBUTES  
{  
   JS_PROPERTY_ATTRIBUTE_NONE = 0,  
   JS_PROPERTY_HAS_CHILDREN = 0x1,  
   JS_PROPERTY_FAKE = 0x2,  
   JS_PROPERTY_METHOD = 0x4,  
   JS_PROPERTY_READONLY = 0x8,  
   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10  
} JS_PROPERTY_ATTRIBUTES;  
```  
  
## 成员  
  
|名称|描述|  
|--------|--------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|属性没有特性。|  
|`JS_PROPERTY_HAS_CHILDREN`|属性具有子级。|  
|`JS_PROPERTY_FAKE`|属性表示一个虚拟节点，例如“\[Methods\]”。|  
|`JS_PROPERTY_METHOD`|此方法已被弃用。|  
|`JS_PROPERTY_READONLY`|该属性是只读的。|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|属性是指向本机 WinRT 对象。|  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)