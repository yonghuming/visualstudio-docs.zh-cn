---
title: "IScriptNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetParent"
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetParent
返回一个对象的父级的 `IScriptNode` 对象。  
  
## 语法  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### 参数  
 `ppsnParent`  
 \[in\]接收指向该父实例的 `IScriptNode` 接口变量的地址。  
  
 如果选件类实现 `IScriptEntry` 或 `IScriptScriptlet`，`IScriptNode` 返回对象。  
  
 如果选件类实现 `IScriptNode`\(表示网页\)，返回NULL。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)