---
title: "加密警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4936482aea909938e135e8f61164955dacc9e20b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="cryptography-warnings"></a>加密警告
加密警告支持通过正确使用加密提高库和应用程序的安全性。 这些警告帮助防止程序中出现安全漏洞。 如果你禁用其中的某个警告，你应当在代码中清楚标出原因，同时将你的开发项目通知指定的安全负责人。  
  
|规则|描述|  
|----------|-----------------|  
|[CA5350：请勿使用弱加密算法](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|出于多种原因，现今使用弱加密算法和哈希函数，但不应使用它们来保证保密性或它们所保护的数据的完整性。        当此规则在代码中找到 TripleDES、SHA1、或 RIPEMD160 算法时，此规则将触发。|  
|[CA5351 不使用损坏的加密算法](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|损坏的加密算法不安全，强烈建议不要使用。 当此规则在代码中找到 MD5 哈希算法，或者 DES 或 RC2 加密算法时，此规则将触发。|