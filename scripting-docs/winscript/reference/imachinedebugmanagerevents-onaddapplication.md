---
title: "IMachineDebugManagerEvents::onAddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerEvents.onAddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerEvents::onAddApplication"
ms.assetid: 00a54b91-36d5-430d-b654-5e2abe5300cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents::onAddApplication
事件的处理，当应用程序添加到列表的运行应用程序。  
  
## 语法  
  
```  
HRESULT onAddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### 参数  
 `pda`  
 \[in\]添加到运行的应用程序的应用程序列表中。  
  
 `dwAppCookie`  
 \[out\]提供的cookie，当应用程序添加到应用程序列表中。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法指示应用程序添加到运行的应用程序列表中。  
  
## 请参阅  
 [IMachineDebugManagerEvents 接口](../../winscript/reference/imachinedebugmanagerevents-interface.md)   
 [IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)