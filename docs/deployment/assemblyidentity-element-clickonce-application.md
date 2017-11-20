---
title: "&lt;assemblyIdentity&gt;元素 （ClickOnce 应用程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: "20"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: db313077fa7903b2bdb2fbbe6b76aa80c940fecd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt;元素 （ClickOnce 应用程序）
标识部署中的应用程序[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `assemblyIdentity`元素是必需的。 它不包含任何子元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`Name`|必需。 标识应用程序的名称。<br /><br /> 如果`Name`包含特殊字符，例如单引号或双引号引号，应用程序可能无法激活。|  
|`Version`|必需。 采用以下格式指定应用程序的版本号：`major.minor.build.revision`|  
|`publicKeyToken`|可选。 指定的 16 个字符的十六进制字符串表示的最后 8 个字节`SHA-1`的应用程序集签名的公钥的哈希值。 用于对目录进行签名的公钥必须是 2048 位或更高版本。<br /><br /> 虽然为程序集签名是可选但建议，此属性是必需的。 如果程序集未签名，你应从自签名的程序集复制值或使用"假"全为零的值。|  
|`processorArchitecture`|必需。 指定处理器。 有效值为`msil`适用于所有处理器`x86`适用于 32 位 Windows`IA64`适用于 64 位 Windows 和`Itanium`Intel 64 位 Itanium 处理器的。|  
|`language`|必需。 标识由两部分语言代码 (例如， `en-US`) 的程序集。 此元素处于`asmv2`命名空间。 如果未指定，默认值是`neutral`。|  
  
## <a name="examples"></a>示例  
  
### <a name="description"></a>描述  
 下面的代码示例阐释了`assemblyIdentity`中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序清单。 此代码示例摘自[ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)。  
  
### <a name="code"></a>代码  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > 元素](../deployment/assemblyidentity-element-clickonce-deployment.md)