---
title: "SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 枚举
显示已引发异常的类型。  此枚举由 [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) 方法使用。  
  
> [!IMPORTANT]
>  这些常量由 PDM 11.0 和更高版本实现。  在 activdbg100.h 中发现。  
  
## 语法  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|ETK\_FIRST\_CHANCE|0x00000000|此异常是首次异常。|  
|ETK\_USER\_UNHANDLED|0x00000001|此异常未在用户代码中进行处理。|  
|ETK\_UNHANDLED|0x00000002|此异常未在代码中进行处理。|  
  
## 请参阅  
 [IActiveScriptErrorDebug110 接口](../../winscript/reference/iactivescripterrordebug110-interface.md)