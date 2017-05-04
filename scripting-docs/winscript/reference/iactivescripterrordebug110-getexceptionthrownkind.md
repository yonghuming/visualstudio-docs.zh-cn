---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
返回用于指示已引发异常的类型的值。  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 接口](../../winscript/reference/iactivescripterrordebug110-interface.md) 由 PDM 11.0 和更高版本实现。  在 activdbg100.h 中发现。  
  
## 语法  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### 参数  
 `pExceptionKind`  
 \[out\] 已引发异常的类型（例如，首次异常或未处理异常），由 [SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND 枚举](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) 枚举值来表示。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括（但并不限于）下表中的项。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 请参阅  
 [IActiveScriptErrorDebug110 接口](../../winscript/reference/iactivescripterrordebug110-interface.md)