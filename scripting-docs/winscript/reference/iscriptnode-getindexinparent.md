---
title: "IScriptNode::GetIndexInParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetIndexInParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetIndexInParent"
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetIndexInParent
返回一个对象的索引在父的子元素的列表。  
  
## 语法  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### 参数  
 `pisn`  
 \[in\]返回一个对象的索引在父的子元素的列表。  
  
 如果此方法由一个表示网页的 `IScriptNode` 对象调用，此参数返回0。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)