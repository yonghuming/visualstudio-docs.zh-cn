---
title: "SCRIPTGCTYPE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTGCTYPE 枚举
垃圾回收的类型执行的。  在 [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) 方法中使用。  
  
## 语法  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## 枚举值  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|常规执行垃圾回收。  整数值为0。|  
|SCRIPTGCTYPE\_EXHAUSTIVE|执行完整垃圾回收。  整数值为1。|  
  
## 请参阅  
 [活动脚本常量、枚举和错误代码](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)