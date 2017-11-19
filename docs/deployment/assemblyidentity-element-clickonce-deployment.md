---
title: "&lt;assemblyIdentity&gt;元素 （ClickOnce 部署） |Microsoft 文档"
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
helpviewer_keywords: <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 26debb7d29458ab6452a2063e8e5c7e2f43fa7d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt;元素 （ClickOnce 部署）
标识的主程序集[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `assemblyIdentity`元素是必需的。 它不包含任何子元素，并具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`name`|必需。 用于信息说明标识部署的用户可读名称。<br /><br /> 如果`name`包含特殊字符，例如单引号或双引号引号，应用程序可能无法激活。|  
|`version`|必需。 采用以下格式指定的程序集的版本号： `major.minor.build.revision`。<br /><br /> 此值必须以触发应用程序更新的更新清单中会递增。|  
|`publicKeyToken`|必需。 指定的 16 字符十六进制字符串，表示在其下的部署清单进行签名的公钥的 sha-1 哈希值的最后 8 个字节。 用于对进行签名的公钥必须是 2048 位或更高版本。<br /><br /> 虽然为程序集签名是可选但建议，此属性是必需的。 如果程序集未签名，你应从自签名的程序集复制值或使用"假"全为零的值。|  
|`processorArchitecture`|必需。 指定处理器。 有效值为`msil`适用于所有处理器`x86`适用于 32 位 Windows`IA64`适用于 64 位 Windows 和`Itanium`Intel 64 位 Itanium 处理器的。|  
|`type`|必需。 有关与 Windows 通过并行安装技术的兼容性。 唯一允许的值是`win32`。|  
  
## <a name="remarks"></a>备注  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`assemblyIdentity`中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署清单。 此代码示例摘自更大的示例为提供[ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)主题。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity > 元素](../deployment/assemblyidentity-element-clickonce-application.md)