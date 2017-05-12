---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject 方法"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
确定对象是否与当前对象相等。  
  
## 语法  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### 参数  
 `punk`  
 \[in\]对象的地址和当前对象进行比较。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|对象相等。|  
|`S_FALSE`|对象不相等。|  
  
## 备注  
 仅当对象相同，`IsEqualObject` 方法的实现应返回 `S_OK`。  
  
## 请参阅  
 [IObjectIdentity 接口](../../winscript/reference/iobjectidentity-interface.md)