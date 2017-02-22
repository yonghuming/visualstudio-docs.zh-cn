---
title: "&lt;assembly&gt; 元素（ClickOnce 部署） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "<assembly> 元素 [ClickOnce 部署清单]"
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;assembly&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

部署清单的顶级元素。  
  
## 语法  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## 元素和特性  
 `assembly` 元素是根元素，因此是必需的。  它包含的第一个元素必须是一个 `assemblyIdentity` 元素。  清单元素必须位于下列命名空间中：`urn:schemas-microsoft-com:asm.v1`、`urn:schemas-microsoft-com:asm.v2` 和 `http://www.w3.org/2000/09/xmldsig#`。  程序集的子元素也必须位于这些命名空间中（通过继承或使用标记）。  
  
 `assembly` 元素具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`manifestVersion`|必选。  此特性必须设置为 `1.0`。|  
  
## 示例  
 下面的代码示例阐释了某应用程序的部署清单中的 `assembly` 元素，该应用程序是使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署的。  此代码示例摘自为 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题提供的一个更大示例。  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly\> 元素](../deployment/assembly-element-clickonce-application.md)