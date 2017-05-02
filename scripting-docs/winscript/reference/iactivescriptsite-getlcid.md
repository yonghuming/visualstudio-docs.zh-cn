---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
检索区域设置标识符与宿主的用户界面。  脚本引擎使用该标识符确保引擎和其他用户界面元素生成的错误字符串出现在相应的语言。  
  
## 语法  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### 参数  
 `plcid`  
 \[in\]接收用户界面元素的区域设置标识符变量的地址被脚本引擎显示。  
  
## 返回值  
 返回下列值之一：  
  
|返回值|含义|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|此方法未实现。  使用系统定义的区域设置。|  
|`E_POINTER`|无效指针指定了。|  
  
## 备注  
 如果此方法返回 `E_NOTIMPL`，应使用系统定义的区域设置标识符。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)