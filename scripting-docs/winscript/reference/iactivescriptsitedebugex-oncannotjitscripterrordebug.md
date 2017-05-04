---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
在处理调试管理器未找到一个实时\(jit\)脚本调试器时，通知脚本运行时错误的。  
  
 若要实现在您的主机上的调试器，您应处理 [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)。  根据用户操作，宿主可以附加调试器并返回，或者返回开始在OnScriptErrorDebug `pfEnterDebugger` 参数的调试器。  还应实现此接口获取有关该运行时错误的注意，即使没有可由进程解释调试管理器的外部调试器。  
  
## 语法  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### 参数  
 `pErrorDebug`  
 \[in\]生成的运行时错误。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[in\]是否调用 [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)，如果用户决定将继续运行，而不调试。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 还应实现此接口获取通知。  
  
## 请参阅  
 [IActiveScriptSiteDebugEx 接口](../../winscript/reference/iactivescriptsitedebugex-interface.md)