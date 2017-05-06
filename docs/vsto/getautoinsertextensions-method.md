---
title: "GetAutoInsertExtensions 方法"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetAutoInsertExtensions 方法
  获取有关在调试期间，将自动插入的apps的信息Office的。  
  
 保留此方法供将来使用。  
  
## 语法  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|*psaExtensionNames*|apps的扩展名称Office的。|  
  
## 返回值  
 一个 HRESULT 值，指示方法是否已成功完成。  
  
## 备注  
 要插入的Office的每个app返回作为Office应用程序扩展名称，对应于值在HKEY\_CURRENT\_USER \\ software \\ Microsoft \\ Office \\ WEF \\开发人员下。  宿主必须自动查找在注册表然后插入的这些值扩展。  
  
  