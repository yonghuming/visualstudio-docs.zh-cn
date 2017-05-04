---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
检索站点对象与Windows脚本引擎。  
  
## 语法  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### 参数  
 `iid`  
 \[in\]请求的接口的标识符。  
  
 `ppvSiteObject`  
 \[in\]接收接口指针到宿主的站点对象位置的地址。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|参数无效。|  
|`E_NOINTERFACE`|这个指定的接口不受支持。|  
|`E_POINTER`|无效指针指定了。|  
|`S_FALSE`|网站尚未设置; `ppvSiteObject` 参数设置为 `NULL`。|  
  
## 请参阅  
 [IActiveScript](../../winscript/reference/iactivescript.md)