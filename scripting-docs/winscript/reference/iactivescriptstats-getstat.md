---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
返回一个标准脚本统计信息。  
  
## 语法  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### 参数  
 `stid`  
 \[in\]用于指定返回的哪个统计信息。  必须为值：  
  
|常量|值|说明|  
|--------|-------|--------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|因为重置，则返回执行的语句数该脚本来启动的或统计信息。|  
  
 `pluHi`  
 \[in\]表示统计信息的64位无符号整数的高32位。  
  
 `pluLo`  
 \[out\]表示统计信息的64位无符号整数的低32位。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值在包括下表中，但不限于值。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回一个标准脚本统计信息。  
  
## 请参阅  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats 接口](../../winscript/reference/iactivescriptstats-interface.md)