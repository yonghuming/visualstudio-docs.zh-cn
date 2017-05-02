---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
返回项的起始位置和长度。  
  
## 语法  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### 参数  
 `pichMin`  
 \[in\]用于指定脚本的 `IScriptEntry` 对象块，则返回0。  
  
 对指定函数对象的 `IScriptEntry` 对象，并返回该函数的起始位置在当前脚本块。  
  
 为 `IScriptScriptlet` 对象，则返回0。  
  
 `pcch`  
 \[in\]用于指定脚本的 `IScriptEntry` 对象块，返回文本的长度。  
  
 对指定函数对象的 `IScriptEntry` 对象，并返回该函数定义的长度。  
  
 为 `IScriptScriptlet` 对象，返回项的长度。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)