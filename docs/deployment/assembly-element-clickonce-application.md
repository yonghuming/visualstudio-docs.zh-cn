---
title: "&lt;assembly&gt; 元素（ClickOnce 应用程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assembly> 元素 [ClickOnce 应用程序清单]"
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# &lt;assembly&gt; 元素（ClickOnce 应用程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

应用程序清单中的顶级元素。  
  
## 语法  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## 元素和特性  
 `assembly` 元素是根元素，因此是必需的。  它包含的第一个元素必须是一个 `assemblyIdentity` 元素。  清单元素必须位于下列命名空间之一：  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 程序集的子元素也必须位于这些命名空间中（通过继承或使用标记）。  
  
 `assembly` 元素具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`manifestVersion`|必选。  `manifestVersion` 特性必须设置为 `1.0`。|  
  
## 示例  
 下面的代码示例阐释 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的应用程序清单中的 `assembly` 元素。  此代码示例摘自为 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)提供的一个更大示例。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
```  
  
## 请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<assembly\> 元素](../deployment/assembly-element-clickonce-deployment.md)