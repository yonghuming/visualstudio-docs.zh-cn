---
title: "IActiveScriptProfilerControl3 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerControl3 接口
提供方法枚举time in GC堆对象与脚本引擎。  
  
## 语法  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## 方法  
 [IActiveScriptProfilerControl3::EnumHeap 方法](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 返回可以用于循环访问GC堆对象在关联的脚本引擎中的接口\([IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\)。