---
title: "IProcessDebugManager::CreateApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateApplication"
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateApplication
创建新调试此应用程序的应用程序对象。  
  
## 语法  
  
```  
HRESULT CreateApplication(  
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
 此方法创建的对象没有名称和不添加到运行的应用程序列表中。  使用 `IProcessDebugManager::AddApplication` 添加调试应用程序添加到应用程序列表中。  
  
## 请参阅  
 [IProcessDebugManager 接口](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)