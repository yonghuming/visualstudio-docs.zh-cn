---
title: "IProcessDebugManager::GetDefaultApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::GetDefaultApplication"
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::GetDefaultApplication
返回当前的默认应用程序对象的过程。  
  
## 语法  
  
```  
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### 参数  
 `ppda`  
 \[in\]此应用程序的调试应用程序对象。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法将创建一个新的调试应用程序对象并将其添加到运行的应用程序列表中，如果需要，。  
  
 语言引擎应使用 `GetDefaultApplication` 方法指定应用程序，则它们在不提供一个应用程序的主机上运行。  
  
## 请参阅  
 [IProcessDebugManager 接口](../../winscript/reference/iprocessdebugmanager-interface.md)