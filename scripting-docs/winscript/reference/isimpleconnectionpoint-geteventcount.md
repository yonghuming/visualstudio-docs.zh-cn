---
title: "ISimpleConnectionPoint::GetEventCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.GetEventCount
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::GetEventCount"
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::GetEventCount
返回此接口公开的事件数。  
  
## 语法  
  
```  
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### 参数  
 `pulCount`  
 \[in\]此接口计数公开的事件数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回此接口公开的事件数。  
  
## 请参阅  
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)