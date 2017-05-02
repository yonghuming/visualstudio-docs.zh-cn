---
title: "IDebugApplication::DebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.DebugOutput
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::DebugOutput"
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::DebugOutput
导致给定字符串由调试器集成开发环境\(IDE\)显示。  
  
## 语法  
  
```  
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### 参数  
 `pstr`  
 \[in\]显示的字符串在调试器。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法允许语言引擎实现特定语言的调试输出支持。  该字符串在调试器的输出窗口通常会显示。  
  
 此方法使 `IApplicationDebugger::onDebugOutput` 调用。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)