---
title: "PROFILER_RELATIONSHIP_INFO 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_RELATIONSHIP_INFO 枚举
表示有关对象的信息在关系。  在 [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md) 中使用。  
  
## 语法  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|对象是数字。|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|对象是字符串。|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|对象是堆对象。|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|对象是外部，也就是说，不在垃圾回收堆。|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|对象是BSTR。|