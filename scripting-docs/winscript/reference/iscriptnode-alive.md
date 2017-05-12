---
title: "IScriptNode::Alive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Alive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Alive"
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptNode::Alive
指示对象是否处于活动状态。  
  
## 语法  
  
```  
HRESULT Alive();  
```  
  
#### 参数  
 该方法不带任何参数。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|"脚本"节点处于活动状态。|  
  
## 备注  
 如果对象不处于活动状态，组件对象模型\(COM\)返回从封送处理代理的错误为调用此方法。  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)