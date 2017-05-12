---
title: "IActiveScriptErrorDebug110 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110 接口"
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptErrorDebug110 接口
向 [IActiveScriptDebug 接口](../../winscript/reference/iactivescriptdebug-interface.md) 添加功能。  此接口由 JavaScript 引擎实现，用于确定为什么会发生 BREAKREASON\_ERROR 事件。  
  
> [!IMPORTANT]
>  此接口由 PDM v11.0 和更高版本实现。  在 activdbg100.h 中发现。  
  
## 方法  
 `IActiveScriptErrorDebug110` 接口公开以下方法。  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|返回某一引发的异常的异常类型。|