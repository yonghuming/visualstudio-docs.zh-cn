---
title: "关于异常的疑难解答：System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException 异常"
  - "UnsupportedPolicyOptionsException 异常"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
<xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> 异常指示已向包含不受支持的选项的系统提供了策略。 下面列举了会导致这些失败的限制：  
  
 接收者已通过指定 http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self 作为标记的发出者，已经从本地安全标记服务请求了标记。 但是，CardSpace 本地安全标记服务不支持策略中指定的某个请求。 有关更多信息，请参见 [Information Card Profile V1.0 技术参考](http://go.microsoft.com/fwlink/?LinkId=102401)。 下面列举了不受支持选项：  
  
-   接收者请求的声明未在“Information Card Profile V1.0 的技术参考”的[受支持的声明类型](http://go.microsoft.com/fwlink/?LinkId=102402)部分中指定的受支持声明的列表中列出。  
  
-   标记类型不是 SAML 1.0 或 1.1。  
  
-   对于非 SSL 网站，密钥并不对称。  
  
-   KeyWrapAlgorithm 不同于默认算法。  
  
-   策略中指定了不受支持的元素。 下面列举了受支持的元素：  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   wst:RequestType 不是 Issue 类型。  
  
-   对于非对称密钥类型，密钥大小不是 2048。  
  
## 请参阅  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)