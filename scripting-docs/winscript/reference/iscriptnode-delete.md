---
title: "IScriptNode::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Delete"
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::Delete
删除此对象树。  
  
## 语法  
  
```  
HRESULT Delete();  
```  
  
#### 参数  
 该方法不带任何参数。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 在 `Delete` 调用方法后，[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) 方法应指示脚本节点不是活动的。  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)