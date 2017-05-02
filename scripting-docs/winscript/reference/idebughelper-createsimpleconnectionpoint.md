---
title: "IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreateSimpleConnectionPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreateSimpleConnectionPoint"
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreateSimpleConnectionPoint
返回包装特定 `IDispatch` 对象的事件接口。  
  
## 语法  
  
```  
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp   
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### 参数  
 `pdisp`  
 \[in\]要包装的 `IDispatch` 对象。  
  
 `ppscp`  
 \[in\]包装 `pdisp`的事件接口。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 返回包装特定 `IDispatch` 的事件接口\(请参见 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)\)。  
  
## 请参阅  
 [IDebugHelper 接口](../../winscript/reference/idebughelper-interface.md)   
 [ISimpleConnectionPoint 接口](../../winscript/reference/isimpleconnectionpoint-interface.md)