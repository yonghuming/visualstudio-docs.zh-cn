---
title: "IDebugSessionProviderEx:CanJITDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:CanJITDebug
apilocation: scrobj.dll
ms.assetid: 68f91bed-ca69-46b5-b517-ca9ca80b8803
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugSessionProviderEx:CanJITDebug
确定指定的是否处理调试与实时\(jit\)调试。  
  
## 语法  
  
```  
HRESULT CanJITDebug(  
   DWORD  pid  
);  
```  
  
#### 参数  
 `pid`  
 \[in\]要调试的进程的进程标识符。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IDebugSessionProviderEx 接口](../../winscript/reference/idebugsessionproviderex-interface.md)