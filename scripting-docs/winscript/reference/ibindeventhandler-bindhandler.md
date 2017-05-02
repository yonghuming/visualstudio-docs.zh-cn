---
title: "IBindEventHandler::BindHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IBindEventHandler::BindHandler"
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IBindEventHandler::BindHandler
将某个事件对象。  
  
## 语法  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### 参数  
 `pstrEvent`  
 \[in\]用于指定事件处理。  
  
 `pdisp`  
 \[in\]用于指定要处理的对象事件。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法将一个操作到对象。  
  
## 请参阅  
 [IBindEventHandler 接口](../../winscript/reference/ibindeventhandler-interface.md)