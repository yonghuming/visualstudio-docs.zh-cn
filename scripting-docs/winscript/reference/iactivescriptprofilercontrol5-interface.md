---
title: "IActiveScriptProfilerControl5 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptProfilerControl5 接口
提供方法以便枚举与脚本引擎关联的 GC 堆对象。  
  
## 语法  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## 方法  
 [IActiveScriptProfilerControl5::EnumHeap2 方法](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 返回可用于在关联的脚本引擎上下文中迭代访问 GC 堆对象的接口 \([IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\)。