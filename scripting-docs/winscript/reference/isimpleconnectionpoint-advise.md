---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
生成简单的之间的连接连接点对象和客户端的接收器。  
  
## 语法  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### 参数  
 `pdisp`  
 \[out\]一个指向 `IDispatch` 接口的指针在客户端的建议接收器。  客户端的接收器接收从简单的出站连接点。  
  
 `pdwCookie`  
 \[out\]一个指向唯一标识此连接的返回标记的指针。  调用方后使用此标记通过将删除连接到 `ISimpleConnectionPoint::Unadvise` 方法。  如果连接未成功生成，此值为零。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法生成简单的之间的连接连接点对象和客户端的接收器。  
  
## 请参阅  
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)