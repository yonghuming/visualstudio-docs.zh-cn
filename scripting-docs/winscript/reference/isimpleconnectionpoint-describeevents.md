---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
返回DISPID和名称每个事件在事件中与指定的范围。  
  
## 语法  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### 参数  
 `iEvent`  
 \[in\]要检索的第一个操作的索引。  
  
 `cEvents`  
 \[in\]要检索的事件数。  
  
 `prgid`  
 \[in\]事件DISPID值。  
  
 `prgbstr`  
 \[in\]事件名称。  
  
 `pcEventsFetched`  
 \[out\]中获取的事件的实际数目。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`S_FALSE`|更多活动多于可用请求。  可用事件由DISPID\_NULL和空BSTR表示形式。|  
|`E_INVALIDARG`|元素不能获取。|  
  
## 备注  
 此方法返回DISPID和名称每个事件在事件中与指定的范围。  
  
## 请参阅  
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)