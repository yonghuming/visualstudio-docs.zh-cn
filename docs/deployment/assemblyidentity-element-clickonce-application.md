---
title: "&lt;assemblyIdentity&gt; 元素（ClickOnce 应用程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<assemblyIdentity> 元素 [ClickOnce 应用程序清单]"
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# &lt;assemblyIdentity&gt; 元素（ClickOnce 应用程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署中部署的应用程序。  
  
## 语法  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## 元素和特性  
 `assemblyIdentity` 元素是必需的。  它不包含任何子元素，且具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Name`|必选。  标识应用程序的名称。<br /><br /> 如果 `Name` 包含特殊字符（如单引号或双引号），应用程序可能无法激活。|  
|`Version`|必选。  指定应用程序的版本号，格式如下：`major.minor.build.revision`|  
|`publicKeyToken`|可选。  指定 16 个字符的十六进制字符串，该字符串表示公钥的 `SHA-1` 哈希值的后 8 个字节。使用该公钥，可以对应用程序或程序集进行签名。  用于对目录进行签名的公钥必须至少为 2048 位。<br /><br /> 对程序集进行签名是可选操作，但建议您这样做；此特性是必需的。  如果程序集未进行签名，则应从自签名程序集复制一个值或使用全为零的“虚拟”值。|  
|`processorArchitecture`|必选。  指定处理器。  适用于所有处理器的有效值是 `msil`，适用于 32 位 Windows 的有效值是 `x86`，适用于 64 位 Windows 的有效值是 `IA64`，适用于 Intel 64 位 Itanium 处理器的有效值是 `Itanium`。|  
|`language`|必选。  标识程序集的两部分语言代码，如 `en-US`。  此元素在 `asmv2` 命名空间中。  如果未指定，则默认值为 `neutral`。|  
  
## 示例  
  
### 说明  
 下面的代码示例阐释了 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序清单中的 `assemblyIdentity` 元素。  此代码示例摘自为 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)提供的一个更大示例。  
  
### 代码  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## 请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity\> 元素](../deployment/assemblyidentity-element-clickonce-deployment.md)