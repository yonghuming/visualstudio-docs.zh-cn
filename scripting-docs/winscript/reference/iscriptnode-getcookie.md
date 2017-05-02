---
title: "IScriptNode::GetCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetCookie
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetCookie"
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IScriptNode::GetCookie
返回用于将scriptlet与宿主对象的应用程序定义的值。  
  
## 语法  
  
```  
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### 参数  
 `pdwCookie`  
 \[in\]用于 `IScriptEntry` 对象，返回应用程序定义的cookie值。  
  
 对一个表示网页的 `IScriptNode` 对象，则返回0。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptNode 接口](../../winscript/reference/iscriptnode-interface.md)