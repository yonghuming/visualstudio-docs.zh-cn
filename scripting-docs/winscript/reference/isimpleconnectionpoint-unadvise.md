---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
终止先前通过 `ISimpleConnectionPoint::Advise` 建立的通知连接。  
  
## 语法  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### 参数  
 `dwCookie`  
 \[in\]停止的连接的标记，如返回从 `ISimpleConnectionPoint::Advise`。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 当具有建议性连接终止时，连接点调用在 `ISimpleConnectionPoint::Advise` 方法中，对于连接保存的指针的 `Release` 方法。  执行在 `ISimpleConnectionPoint::Advise` 过程中它称为反转 `AddRef`，在连接点上调用具有建议性接收器的 `QueryInterface`时。  
  
## 请参阅  
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)