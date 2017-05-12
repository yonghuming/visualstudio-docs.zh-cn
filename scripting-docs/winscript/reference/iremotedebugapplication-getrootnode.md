---
title: "IRemoteDebugApplication::GetRootNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetRootNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetRootNode"
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetRootNode
返回下所有节点与应用程序添加的应用程序节点。  
  
## 语法  
  
```  
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### 参数  
 `ppdanRoot`  
 \[out\]下所有节点与应用程序添加到的调试应用程序节点。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回下所有节点与应用程序添加的应用程序节点。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)