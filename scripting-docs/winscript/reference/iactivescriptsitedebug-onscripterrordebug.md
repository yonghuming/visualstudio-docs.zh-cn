---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
如何允许一个智能宿主确定处理运行时错误。  
  
## 语法  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### 参数  
 `pErrorDebug`  
 \[in\]生成的运行时错误  
  
 `pfEnterDebugger`  
 \[in\]则应标记指示通过该错误并使调试器执行JIT调试。  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[in\]则应标记指示调用 `IActiveScriptSite::OnScriptError`，当用户选择继续时，不调试。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值在包括下表中，但不限于值。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 一个智能宿主如何使用此方法来确定处理运行时错误。  
  
## 请参阅  
 [IActiveScriptSiteDebug 接口](../../winscript/reference/iactivescriptsitedebug-interface.md)