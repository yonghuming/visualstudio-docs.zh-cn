---
title: "IRemoteDebugApplication::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.EnumThreads
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::EnumThreads"
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::EnumThreads
枚举已知的所有线程都与应用程序。  
  
## 语法  
  
```  
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### 参数  
 `pperdat`  
 \[in\]列出了已知的所有线程都与应用程序的枚举器。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法枚举已知的所有线程都与应用程序。  新线程可以在\+任何\+时间添加。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)