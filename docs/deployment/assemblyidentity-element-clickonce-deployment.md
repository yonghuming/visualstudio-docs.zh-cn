---
title: "&lt;assemblyIdentity&gt; 元素（ClickOnce 部署） | Microsoft Docs"
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
  - "<assemblyIdentity> 元素 [ClickOnce 部署清单]"
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;assemblyIdentity&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标识 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 应用程序的主程序集。  
  
## 语法  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## 元素和特性  
 `assemblyIdentity` 元素是必需的。  它不包含任何子元素，且具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`name`|必选。  标识部署的可读名称，以达到提供信息的目的。<br /><br /> 如果 `name` 包含特殊字符（如单引号或双引号），应用程序可能无法激活。|  
|`version`|必选。  按如下格式指定程序集的版本号：`major.minor.build.revision`。<br /><br /> 必须在更新的清单中增大此值，才能触发应用程序更新。|  
|`publicKeyToken`|必选。  指定一个 16 字符的十六进制字符串，该字符串表示公钥的 SHA\-1 哈希值的后 8 个字节，该公钥用于对部署清单进行签名。  用于签名的公钥必须至少为 2048 位。<br /><br /> 对程序集进行签名是可选操作，但建议您这样做；此特性是必需的。  如果程序集未进行签名，则应从自签名程序集复制一个值或使用全为零的“虚拟”值。|  
|`processorArchitecture`|必选。  指定处理器。  适用于所有处理器的有效值是 `msil`，适用于 32 位 Windows 的有效值是 `x86`，适用于 64 位 Windows 的有效值是 `IA64`，适用于 Intel 64 位 Itanium 处理器的有效值是 `Itanium`。|  
|`type`|必选。  用于与 Windows 并行安装技术的兼容性。  唯一允许的值是 `win32`。|  
  
## 备注  
  
## 示例  
 下面的代码示例阐释了 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署清单中的 `assemblyIdentity` 元素。  此代码示例摘自为 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题提供的一个更大示例。  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity\> 元素](../deployment/assemblyidentity-element-clickonce-application.md)