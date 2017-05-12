---
title: "IRemoteDebugApplicationEx:SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:SetLocale
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:SetLocale"
ms.assetid: cd19f725-f4cd-453a-95e1-0bad676451da
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:SetLocale
设置调试器本地化的语言。  
  
## 语法  
  
```  
HRESULT SetLocale(  
   DWORD  dwLangID  
);  
```  
  
#### 参数  
 `dwLangID`  
 \[in\]语言ID.  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
  
## 请参阅  
 [ISetNextStatement 接口](../../winscript/reference/isetnextstatement-interface.md)