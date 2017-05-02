---
title: "IScriptEntry::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetText"
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetText
返回对应于 `IScriptEntry` 脚本块或源代码。`IScriptScriptlet` 事件处理程序中包含的文本。  
  
## 语法  
  
```  
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### 参数  
 `pbstr`  
 \[out\]在 `IScriptEntry` 脚本的文本块或在 `IScriptScriptlet` 事件处理程序包含的源代码。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)