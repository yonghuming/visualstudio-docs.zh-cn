---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
返回位于节点的指定索引处的子级。  
  
## 语法  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### 参数  
 `isn`  
 \[in\]\)的索引父级。  
  
 `ppsn`  
 \[in\]接收指向该子实例的 `IScriptNode` 接口变量的地址。  
  
 对一个表示网页的 `IScriptNode` 对象，此参数返回一个脚本块的对象。  
  
 对于指定脚本的 `IScriptEntry` 对象块，此参数返回指定函数的对象。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 为 `IScriptScriptlet` 对象指定函数对象和的 `IScriptEntry` 对象，此方法失败，因为没有子项。  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)