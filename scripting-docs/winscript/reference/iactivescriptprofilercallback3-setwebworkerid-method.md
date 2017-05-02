---
title: "IActiveScriptProfilerCallback3::SetWebWorkerId 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerCallback3::SetWebWorkerId 方法
通知辅助ID的探查器为此分析会话使用。  如果函数不执行页中，该方法未调用。  `webWorkerId` 的值由1增加每个辅助的，从1开始。  ID值不是稳定在会话以外，只有对应于辅助创建的顺序。  
  
## 语法  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### 参数  
 `webWorkerId`  
 web辅助ID.  
  
## 返回值  
 此方法的返回值由脚本引擎忽略。