---
title: "IActiveScriptSiteDebugEx 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx 接口"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx 接口
请与 `IActiveScriptSiteDebug` 接口的实现此接口，如果要编写需要获取一个运行时错误通知在应用程序的主机和选择性地附加到进行调试。  如果一台实时脚本调试器计算机上，找到处理调试管理器通过 `IActiveScriptDebug` 提供通知。  如果未找到实时脚本调试器，PDM通过 `IActiveScriptDebugEx` 提供通知。  
  
 获取一个运行时错误的通知，则宿主必须处理 [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/zh-cn/cf7639f9-a699-4571-9f3a-82ef52c0b5f4)。  根据用户操作，您可以决定附加内部调试器并返回，或者返回开始在OnScriptErrorDebug `pfEnterDebugger` 参数的调试器。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|在处理调试管理器未找到外部实时\(jit\)调试器时，通知脚本运行时错误的。|