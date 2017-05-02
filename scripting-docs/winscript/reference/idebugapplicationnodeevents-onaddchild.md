---
title: "IDebugApplicationNodeEvents::onAddChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAddChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAddChild"
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAddChild
处理事件，当子节点添加到调试应用程序节点对象。  
  
## 语法  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### 参数  
 `prddpChild`  
 \[in\]子级调试后添加的应用程序节点。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法处理事件，当子节点添加到调试应用程序节点对象。  
  
 `IDebugApplicationNode` 接口的实现引发此事件  
  
## 请参阅  
 [IDebugApplicationNodeEvents 接口](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)