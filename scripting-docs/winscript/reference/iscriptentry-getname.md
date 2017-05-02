---
title: "IScriptEntry::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetName"
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::GetName
为表示单个对象的项\(如函数\)，返回对象的名称。  
  
## 语法  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### 参数  
 `pbstr`  
 \[out\] `IScriptEntry` 脚本表示的对象的名称块。  如果项不表示一个对象，返回NULL。  
  
 子项表示单个功能对象。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)