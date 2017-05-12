---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
检索下 `IDispError` 对象。  
  
## 语法  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### 参数  
 `ppde`  
 \[in\]用于指定下 `IDispError` 对象。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法检索下 `IDispError` 对象。  如果这是最后 `IDispError` 对象，此方法返回NULL。  
  
> [!NOTE]
>  此方法未实现。  
  
## 请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)