---
title: "IScriptScriptlet::SetSimpleEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSimpleEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSimpleEventName"
ms.assetid: 7de9132e-635f-45df-9c92-83a24242b477
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IScriptScriptlet::SetSimpleEventName
设置与scriptlet的简单事件名称。  这是不包含任何空白的单个符名称。  
  
## 语法  
  
```  
HRESULT SetSimpleEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### 参数  
 `psz`  
 \[in\]包含简单的事件名称与 `IScriptScriptlet` 对象的缓冲区。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptScriptlet 接口](../../winscript/reference/iscriptscriptlet-interface.md)