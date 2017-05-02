---
title: "IDebugApplication::FireDebuggerEvent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FireDebuggerEvent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FireDebuggerEvent"
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FireDebuggerEvent
激发泛型事件对调试器的 `IApplicationDebugger` 接口。  
  
## 语法  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### 参数  
 `riid`  
 \[in\]对象的GUID。  
  
 `punk`  
 \[in\]传递的事件对象到调试器。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|方法当前未执行。|  
  
## 备注  
 完全是应用程序\/调试器中定义的GUID的语义和 `IUnknown`。  
  
 此方法允许调试器模型的自定义扩展;它当前未实现。  
  
 此方法使 `IApplicationDebugger::onDebuggerEvent` 调用。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)