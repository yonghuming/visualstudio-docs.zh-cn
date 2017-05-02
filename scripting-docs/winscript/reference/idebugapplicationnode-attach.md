---
title: "IDebugApplicationNode::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::Attach"
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::Attach
将此应用程序节点到指定的项目树。  
  
## 语法  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### 参数  
 `pdanParent`  
 \[in\]项树此应用程序节点将添加的。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法将此应用程序节点到项目树，使用 `pdanParent` 作为父级。  如果 `pdanParent` 是 `NULL`，此应用程序节点是顶级节点。  
  
## 请参阅  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)