---
title: "&lt;程序集&gt;元素 （ClickOnce 应用程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fafc5df1a2aa32fa60c1f41077f7e3fff29ddef7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;程序集&gt;元素 （ClickOnce 应用程序）
应用程序清单的的顶级元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <assembly  
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>元素和属性  
 `assembly`元素是根元素，它需要。 其第一个包含的元素必须是`assemblyIdentity`元素。 清单元素必须在以下命名空间之一：  
  
 `urn:schemas-microsoft-com:asm.v1`  
  
 `urn:schemas-microsoft-com:asm.v2`  
  
 `http://www.w3.org/2000/09/xmldsig#`  
  
 程序集的子元素也必须通过继承或使用标记这些命名空间中。  
  
 `assembly`元素具有以下属性。  
  
|特性|说明|  
|---------------|-----------------|  
|`manifestVersion`|必需。 `manifestVersion`属性必须设置为`1.0`。|  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`assembly`的应用程序清单中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]应用程序。 此代码示例摘自[ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)   
 [\<程序集 > 元素](../deployment/assembly-element-clickonce-deployment.md)