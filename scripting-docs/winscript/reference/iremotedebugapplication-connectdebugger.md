---
title: "IRemoteDebugApplication::ConnectDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.ConnectDebugger
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::ConnectDebugger"
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::ConnectDebugger
连接一个调试器附加到此应用程序。  
  
## 语法  
  
```  
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### 参数  
 `pad`  
 \[in\]附加调试器附加到此应用程序。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|调试器已连接到此应用程序。|  
  
## 备注  
 应用程序只能有每个连接的一个调试器。  如果调试器已连接，此方法失败。  
  
## 请参阅  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)