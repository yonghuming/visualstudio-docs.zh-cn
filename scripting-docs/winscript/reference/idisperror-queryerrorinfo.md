---
title: "IDispError::QueryErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::QueryErrorInfo"
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::QueryErrorInfo
检索错误信息的特定类型。  
  
## 语法  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### 参数  
 `guidErrorType`  
 \[in\]用于指定错误类型的GUID。  
  
 `ppde`  
 \[in\]用于指定IDispError对象。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 `QueryErrorInfo` 方法检索错误信息的特定类型。  
  
> [!NOTE]
>  此方法未实现。  
  
## 请参阅  
 [IDispError 接口](../../winscript/reference/idisperror-interface.md)