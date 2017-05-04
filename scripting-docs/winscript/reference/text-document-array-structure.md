---
title: "TEXT_DOCUMENT_ARRAY 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "TEXT_DOCUMENT_ARRAY 结构"
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# TEXT_DOCUMENT_ARRAY 结构
[IDebugDocumentText 接口](../../winscript/reference/idebugdocumenttext-interface.md) 对象的数组。  成员随CoTaskMemAlloc。  
  
## 语法  
  
```  
typedef struct tagTEXT_DOCUMENT_ARRAY  
{  
    DWORD dwCount;  
    [size_is(dwCount)] IDebugDocumentText **Members;  
} TEXT_DOCUMENT_ARRAY;  
  
```  
  
## 成员  
 `dwCount`  
 文档数目。  
  
 `Members`  
 设置文档。  
  
## 请参阅  
 [活动脚本调试器常量、枚举和结构](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)