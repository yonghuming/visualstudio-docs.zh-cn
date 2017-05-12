---
title: "IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptSiteTraceInfo::SendScriptTraceInfo 方法
发送包含事件类型、上下文和脚本语句的跟踪信息。  
  
## 语法  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### 参数  
 `stiEventType`  
 事件类型。  
  
 `guidContextId`  
 上下文的 GUID。  
  
 `dwScriptContextCookie`  
 上下文的 cookie。  
  
 `lScriptStatementStart`  
 脚本语句开始的位置。  
  
 `lScriptStatementEnd`  
 脚本语句的结尾的位置。  
  
 `dwReserved`  
 保留。