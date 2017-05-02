---
title: "IDebugApplicationNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.GetParent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::GetParent"
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::GetParent
返回此应用程序节点父节点。  
  
## 语法  
  
```  
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### 参数  
 `pprddp`  
 \[in\]请父此应用程序节点应用程序节点。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回此应用程序节点父节点。  
  
## 请参阅  
 [IDebugApplicationNode 接口](../../winscript/reference/idebugapplicationnode-interface.md)