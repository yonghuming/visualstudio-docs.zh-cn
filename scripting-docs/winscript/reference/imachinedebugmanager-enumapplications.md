---
title: "IMachineDebugManager::EnumApplications | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::EnumApplications"
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::EnumApplications
返回当前的枚举数列表运行应用程序。  
  
## 语法  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### 参数  
 `ppeda`  
 \[in\]包含当前的枚举数列表运行应用程序。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回当前的枚举数列表运行应用程序。  调试器IDE使用此方法显示和附加应用程序用于调试目的。  
  
## 请参阅  
 [IMachineDebugManager 接口](../../winscript/reference/imachinedebugmanager-interface.md)