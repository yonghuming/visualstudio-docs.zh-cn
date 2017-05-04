---
title: "SetWefProcessId 方法 | Microsoft Docs"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# SetWefProcessId 方法
  提供将运行Web扩展框架\(WEF\)内容的进程标识符。  
  
## 语法  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|*dwProcessId*|将用于运行WEF内容的进程标识符。|  
  
## 返回值  
 一个 HRESULT 值，指示方法是否已成功完成。  
  
## 备注  
 必须调用此方法，在WEF内容过程创建后，但，在所有WEF目录运行之前。  
  
 如果要开发环境将调试器附加到WEF目录中，则该环境必须执行此操作在的此方法的实现。  
  
  