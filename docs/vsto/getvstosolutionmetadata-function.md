---
title: "GetVstoSolutionMetadata 函数"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# GetVstoSolutionMetadata 函数
  此API支持Office基础结构并且不应在代码中直接使用。  
  
## 语法  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|*lpwszSolutionMetadataKey*|不要使用。|  
|*ppSolutionInfo*|不要使用。|  
  
## 返回值  
 如果函数成功，则返回 **S\_OK**。  如果函数运行失败，将返回错误代码。  
  
  