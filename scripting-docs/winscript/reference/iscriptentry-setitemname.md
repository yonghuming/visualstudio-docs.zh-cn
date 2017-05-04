---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
设置标识一 `IScriptEntry` 对象的项目名称。  
  
## 语法  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### 参数  
 `psz`  
 \[in\]包含项目名称缓冲区的地址。  宿主用于项目名称标识该项。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|方法不成功。|  
  
## 备注  
 为 `IScriptEntry` 对象，此方法返回 `S_OK`。  
  
 对于从 `IScriptEntry`派生\)的 `IScriptScriptlet` 对象\(，此方法返回 `E_FAIL`。  对于 `IScriptScriptlet` 对象，项目名称由 [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) 设置，并且不能更改。  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)