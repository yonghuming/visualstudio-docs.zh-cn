---
title: "IJsDebugBreakPoint::Disable 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::Disable 方法
禁用断点。  
  
## 语法  
  
```  
HRESULT Disable(void);  
```  
  
## 返回值  
  
## 备注  
 如果对已删除的断点调用，则返回 E\_UNEXPECTED。  如果对已停用的断点调用，则返回 S\_FALSE。  
  
## 要求  
 **标头：**jscript9diag.h  
  
## 请参阅  
 [IJsDebugBreakPoint 接口](../../winscript/reference/ijsdebugbreakpoint-interface.md)