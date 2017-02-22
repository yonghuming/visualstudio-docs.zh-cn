---
title: "&lt;publisherIdentity&gt; 元素（ClickOnce 部署） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publisherIdentity 元素 [ClickOnce 部署清单], 介绍"
  - "publisherIdentity 元素 [ClickOnce 部署清单], 语法, 元素, 和特性"
  - "签名清单所必需的元素 [ClickOnce], publisherIdentity 元素"
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;publisherIdentity&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含有关为此部署清单签名的发布者的信息。  
  
## 语法  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## 元素和特性  
 `publisherIdentity` 元素是签名的清单所必需的。  下表显示了 `publisherIdentity` 元素支持的特性。  
  
|特性|说明|  
|--------|--------|  
|`name`|必选。  说明此应用程序发布方的标识。|  
|`issuerKeyHash`|必选。  包含证书颁发者的公钥的 SHA\-1 哈希。|  
  
#### 参数  
  
## 属性值\/返回值  
  
## 异常  
  
## 备注  
  
## 要求  
  
## 子标题