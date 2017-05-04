---
title: "IDispError::GetHresult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHresult"
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHresult
从 `IDispError` 对象检索错误代码。  
  
## 语法  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### 参数  
 `phr`  
 \[in\]用于指定错误代码。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法从 `IDispError` 对象检索错误代码。  
  
> [!NOTE]
>  此方法未实现。  
  
## 请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)