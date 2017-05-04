---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
通知宿主提供的脚本引擎 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 接口站点。  在使用之前，调用此方法任何其他 [IActiveScript](../../winscript/reference/iactivescript.md) 接口方法。  
  
## 语法  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### 参数  
 `pScriptSite`  
 \[out\]将关联的由宿主提供的脚本网站的地址与脚本引擎的此实例。  必须单独将该站点添加到此脚本引擎实例;它不能与其他脚本引擎共享。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_FAIL`|一个未指定的错误的;脚本引擎无法完成初始化该站点。|  
|`E_INVALIDARG`|参数无效。|  
|`E_POINTER`|无效指针指定了。|  
|`E_UNEXPECTED`|调用非预期\(例如，网站已设置\)。|  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)