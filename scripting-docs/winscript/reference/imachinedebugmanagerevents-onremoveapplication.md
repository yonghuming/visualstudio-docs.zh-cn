---
title: "IMachineDebugManagerEvents::onRemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerEvents.onRemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerEvents::onRemoveApplication"
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents::onRemoveApplication
事件的处理，当应用程序从列表中运行的应用程序中移除。  
  
## 语法  
  
```  
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### 参数  
 `pda`  
 \[in\]运行的应用程序中移除的应用程序列表中。  
  
 `dwAppCookie`  
 \[out\]提供的cookie，当应用程序从应用程序已添加列表。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法指示应用程序从运行的应用程序中移除列表。  
  
## 请参阅  
 [IMachineDebugManagerEvents 接口](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)