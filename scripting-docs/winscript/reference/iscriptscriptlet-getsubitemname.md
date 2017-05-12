---
title: "IScriptScriptlet::GetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSubItemName"
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptScriptlet::GetSubItemName
返回在scriptlet的对象承载的完全限定名的最后一个标识符。  
  
## 语法  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### 参数  
 `pbstr`  
 \[out\]，如果宿主的完全限定scriptlet名称具有多个级别，`pbstr` 返回标识符的缓冲区地址在第二个级别。  
  
 如果主机的完全限定scriptlet名中有一个级别，`pbstr` 返回标识符的缓冲区中的第一个级别。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptScriptlet 接口](../../winscript/reference/iscriptscriptlet-interface.md)