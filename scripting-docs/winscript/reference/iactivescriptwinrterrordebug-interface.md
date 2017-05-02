---
title: "IActiveScriptWinRTErrorDebug 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptWinRTErrorDebug 接口"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptWinRTErrorDebug 接口
实现由JavaScript引擎提供从 [BREAKREASON 枚举](../../winscript/reference/breakreason-enumeration.md) 事件的扩展的Windows运行时错误信息。  可以执行QI获取其从 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) 对象。  
  
> [!IMPORTANT]
>  此接口由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 方法  
 `IActiveScriptWinRTErrorDebug` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|如果有返回Windows运行时错误的功能SID，。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|如果有返回该Windows运行时的限制的错误引用字符串，。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|如果有返回Windows运行时的限制的错误字符串，。|