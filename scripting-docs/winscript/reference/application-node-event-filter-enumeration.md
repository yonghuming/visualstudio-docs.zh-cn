---
title: "APPLICATION_NODE_EVENT_FILTER 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER 常量"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# APPLICATION_NODE_EVENT_FILTER 枚举
在指定节点类型筛选排除代码文档。  使用在 [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 和 [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  这些常量由PDM v10.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## 成员  
  
|成员|值|说明|  
|--------|-------|--------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|发送任何操作。|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|排除匿名代码节点。  JScript运行时使用这些节点。`new Function([args,] <code>)'`。|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|排除eval代码节点。  JScript运行时使用这些节点。eval支持。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)