---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
通知宿主实现发生错误，当引擎运行该脚本时。  
  
## 语法  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### 参数  
 `pase`  
 \[in\]错误对象的 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) 接口的地址。  宿主可以使用此接口来获得有关执行错误的信息。  
  
## 返回值  
 返回 `S_OK`，如果错误得到正确处理的，或OLE否则定义错误代码。  
  
## 请参阅  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)