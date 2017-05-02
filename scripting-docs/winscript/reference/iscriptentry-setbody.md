---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
将 `IScriptEntry` 脚本块体的文本或 `IScriptScriptlet` scriptlet。  
  
## 语法  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### 参数  
 `psz`  
 \[in\]用于 `IScriptEntry` 脚本块，`psz` 是在脚本标记内的文本。  
  
 对于 `IScriptEntry` 功能块，`psz` 是函数的主体。  
  
 对于从 `IScriptEntry`派生\)的 `IScriptScriptlet` 对象\(，`psz` 是scriptlet的脚本文本。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)