---
title: "PROFILER_RELATIONSHIP_INFO 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f01ca5e001d45907af70b46b6dc362e8ae0b2044
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="profilerrelationshipinfo-enumeration"></a>PROFILER_RELATIONSHIP_INFO 枚举
表示关系中的对象有关的信息。 在中使用[PROFILER_HEAP_OBJECT_RELATIONSHIP 结构](../../winscript/reference/profiler-heap-object-relationship-structure.md)。  
  
## <a name="syntax"></a>语法  
  
```  
typedef [v1_enum] enum {    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,    PROFILER_PROPERTY_TYPE_STRING = 0x02,    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,    PROFILER_PROPERTY_TYPE_BSTR = 0x05,} PROFILER_RELATIONSHIP_INFO;  
```  
  
## <a name="members"></a>成员  
  
|成员|值|描述|  
|------------|-----------|-----------------|  
|PROFILER_PROPERTY_TYPE_NUMBER|0x01|对象是一个数字。|  
|PROFILER_PROPERTY_TYPE_STRING|0x02|对象是一个字符串。|  
|PROFILER_PROPERTY_TYPE_HEAP_OBJECT|0x03|对象是堆对象。|  
|PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT|0x04，则|对象不外部，即，在垃圾回收堆上。|  
|PROFILER_PROPERTY_TYPE_BSTR|0x05|对象是 BSTR。|  
|PROFILER_PROPERTY_TYPE_SUBSTRING|0x06|对象是子字符串。|