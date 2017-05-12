---
title: "IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateDebugDocumentHelper"
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateDebugDocumentHelper
创建新调试文档此应用程序的帮助器。  
  
## 语法  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### 参数  
 `punkOuter`  
 \[in\]，则返回的对象将聚合，`punkOuter` 是接口指针。控件 `IUnknown`。  否则，为null指针。  
  
 `pddh`  
 \[in\]调试文档此应用程序的帮助器对象。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法将创建一个新的调试文档此应用程序的帮助器。  
  
## 请参阅  
 [IProcessDebugManager 接口](../../winscript/reference/iprocessdebugmanager-interface.md)