---
title: "IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FIsAutoJitDebugEnabled"
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FIsAutoJitDebugEnabled
确定一个点\(JIT\)调试器是否注册自动调试沉默寡言的主机。  
  
## 语法  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 如果方法成功，跳过JIT调试器注册自动调试沉默寡言的主机，该方法返回 `TRUE`。  否则，该调用将返回 `FALSE`。  
  
## 备注  
 此方法确定JIT调试器是否注册自动调试沉默寡言的主机。  
  
## 请参阅  
 [IDebugApplication 接口](../../winscript/reference/idebugapplication-interface.md)