---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
返回对应于 `IScriptEntry` 脚本块体的文本，功能块或scriptlet。  
  
## 语法  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### 参数  
 `pbstr`  
 \[out\]在主体下列操作之一的文本：  
  
-   `IScriptEntry` 脚本块  
  
-   在函数的一个 `IScriptEntry` 功能块  
  
-   `IScriptEntry` scriptlet事件处理程序  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)