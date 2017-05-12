---
title: "IActiveScriptTraceInfo::StartScriptTracing 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptTraceInfo::StartScriptTracing 方法
开始脚本跟踪。  
  
## 语法  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### 参数  
 `pSiteTraceInfo`  
 对主机的IActiveScriptSiteTraceInfo的指针。  
  
 `guidContextId`  
 上下文的GUID。  
  
## 返回值  
 可以返回此方法的值如下：  
  
1.  S\_OK:成功。  
  
2.  E\_POINTER: `pSiteTraceInfo` 为NULL指针。  
  
3.  E\_NOTIMPL:未实现。