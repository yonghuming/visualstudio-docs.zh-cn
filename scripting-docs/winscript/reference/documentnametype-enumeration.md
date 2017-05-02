---
title: "DOCUMENTNAMETYPE 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE 枚举"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DOCUMENTNAMETYPE 枚举
描述键入文档的访问。  
  
## 语法  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## 成员  
  
|成员|说明|  
|--------|--------|  
|DOCUMENTNAMETYPE\_APPNODE|当出现在应用程序中，获取该名称。|  
|DOCUMENTNAMETYPE\_TITLE|它显示在浏览器标题栏，获取该名称。|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|获取文件名，而无需路径。|  
|DOCUMENTNAMETYPE\_URL|获取文档的 URL。|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|获取标题追加了确定的枚举。|  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)