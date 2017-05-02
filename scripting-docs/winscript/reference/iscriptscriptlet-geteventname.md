---
title: "IScriptScriptlet::GetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetEventName"
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IScriptScriptlet::GetEventName
返回事件的名称与scriptlet。  
  
## 语法  
  
```  
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### 参数  
 `pbstr`  
 \[in\]一个与 `IScriptScriptlet` 对象的缓冲区。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptScriptlet 接口](../../winscript/reference/iscriptscriptlet-interface.md)