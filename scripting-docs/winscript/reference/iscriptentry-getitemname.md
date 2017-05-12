---
title: "IScriptEntry::GetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetItemName"
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::GetItemName
返回标识一 `IScriptEntry` 对象的项目名称。  
  
## 语法  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### 参数  
 `pbstr`  
 \[in\]包含项目名称缓冲区的地址。  宿主用于项目名称标识该项。  
  
## 返回值  
 一个 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 使用 [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)，对于 `IScriptScriptlet` 对象，请设置项目名称。  使用 [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)，对于所有其他接口，则设置项目名称。  
  
## 请参阅  
 [IScriptEntry 接口](../../winscript/reference/iscriptentry-interface.md)