---
title: "&lt;签名&gt;元素 （ClickOnce 部署） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a60156c77dfc33475d3913c3fed2e30159f03959
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;签名&gt;元素 （ClickOnce 部署）
包含对此部署清单进行数字签名所需的信息。  
  
## <a name="syntax"></a>语法  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>备注  
 通过封装签名的部署清单签名是可选的但建议。 有关签名 XML 文件，请参阅 World Wide Web 联合会建议，"XML 签名语法和处理，"中所述[http://www.w3.org/TR/xmldsig-core/](http://www.w3.org/TR/xmldsig-core/)。  
  
 如果你想要对清单签名，则必须为所有文件提供哈希。 不能被签名不哈希处理的文件的清单进行，因为用户无法验证未经哈希的文件的内容。  
  
## <a name="example"></a>示例  
 下面的代码示例阐释了`Signature`中使用的部署清单中的元素[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>另请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)