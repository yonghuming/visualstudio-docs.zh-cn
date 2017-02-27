---
title: "&lt;Signature&gt; 元素（ClickOnce 部署） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<Signature> 元素 [ClickOnce 部署清单]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;Signature&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

包含对此部署清单进行数字签名所需的信息。  
  
## 语法  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## 备注  
 使用封装签名对部署清单进行签名是可选操作，但建议您这样做。  有关对 XML 文件进行签名的更多信息，请参见位于 [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/) 上的 World Wide Web Consortium Recommendation（万维网联合会建议）“XML\-Signature Syntax and Processing”（XML 签名语法与处理）。  
  
 如果要对清单进行签名，必须为所有文件提供哈希。  不能对包含未散列文件的清单进行数字签名，因为用户无法验证未散列文件的内容。  
  
## 示例  
 下面的代码示例阐释 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署所用的部署清单中的 `Signature` 元素。  
  
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
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)