---
title: "IDebugApplication::FCanJitDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FCanJitDebug"
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FCanJitDebug
确定一个点\(JIT\)调试器是否注册。  
  
## 语法  
  
```  
BOOL FCanJitDebug();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 如果方法成功，跳过JIT调试器注册，则该方法返回 `TRUE`。  否则，该调用将返回 `FALSE`。  
  
## 备注  
 此方法确定JIT调试器是否注册。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)