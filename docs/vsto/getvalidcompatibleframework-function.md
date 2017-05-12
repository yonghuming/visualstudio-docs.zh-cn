---
title: "GetValidCompatibleFramework 函数"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# GetValidCompatibleFramework 函数
  此API支持Office基础结构并且不应在代码中直接使用。  
  
## 语法  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|*lpwszCompatibleFrameworksXML*|不要使用。|  
|*pbstrValidFrameworkTag*|不要使用。|  
  
## 返回值  
 如果函数成功，则返回 **S\_OK**。  如果函数运行失败，将返回错误代码。  
  
  