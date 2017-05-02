---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
返回一个自定义脚本统计信息。  
  
## 语法  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### 参数  
 `guid`  
 \[in\]用于指定返回的哪个统计信息。  统计信息对应于特定GUID完全是引擎中定义的语义。  
  
 `pluHi`  
 \[in\]表示统计信息的64位无符号整数的高32位。  
  
 `pluLo`  
 \[out\]表示统计信息的64位无符号整数的低32位。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|此方法未实现。|  
  
## 备注  
 此方法允许自定义脚本引擎返回统计信息有意义到自定义宿主。  
  
> [!NOTE]
>  此方法目前尚未实现。  
  
## 请参阅  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats 接口](../../winscript/reference/iactivescriptstats-interface.md)