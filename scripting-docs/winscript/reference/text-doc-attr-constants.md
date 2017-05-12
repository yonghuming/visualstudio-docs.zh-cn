---
title: "TEXT_DOC_ATTR 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: TEXT_DOC_ATTR
apilocation: scrobj.dll
helpviewer_keywords: 
  - "TEXT_DOC_ATTR 常量"
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# TEXT_DOC_ATTR 常量
描述文档的属性。  
  
## 语法  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## 常量  
  
|常量|值|说明|  
|--------|-------|--------|  
|TEXT\_DOC\_ATTR\_READONLY|0x00000001|文档为只读。|  
|TEXT\_DOC\_ATTR\_TYPE\_PRIMARY|0x00000002|文档是此的主文档树。|  
|TEXT\_DOC\_ATTR\_TYPE\_WORKER|0x00000004|文档是辅助。|  
|TEXT\_DOC\_ATTR\_TYPE\_SCRIPT|0x00000008|文档这些脚本文件。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)