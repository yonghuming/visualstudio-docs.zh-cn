---
title: "IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::GetExcludedDocuments"
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::GetExcludedDocuments
获取文本文档所指定的筛选器隐藏。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 接口](../../winscript/reference/idebugapplicationnode100-interface.md) 由PDM v10.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT GetExcludedDocuments(  
        [in] APPLICATION_NODE_EVENT_FILTER filter,  
        [out] TEXT_DOCUMENT_ARRAY* pDocuments  
        );  
```  
  
#### 参数  
 `filter`  
 筛选器。  
  
 `pDocuments`  
 设置文档。  
  
## 请参阅  
 [IDebugApplicationNode100 接口](../../winscript/reference/idebugapplicationnode100-interface.md)