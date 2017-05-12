---
title: "IActiveScriptDebug 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug 接口"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug 接口
实现支持调试的脚本引擎。  通常，对象实现 `IActiveScriptDebug` 接口来实现 `IActiveScript` 接口。  如果是这样，请调用 `IActiveScript::QueryInterface` 方法获取 `IActiveScriptDebug` 接口。  
  
 `IActiveScriptDebug` 接口提供：  
  
-   获取的智能宿主文件管理。  
  
-   过程调试管理器同步多个脚本引擎调试。  
  
 除了从 `IUnknown` 继承的方法之外，`IActiveScriptDebug` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|返回任意的文本特性块脚本文本。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|返回任意scriptlet的文本属性。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|`IDebugDocumentContext::EnumCodeContexts`的委托。|