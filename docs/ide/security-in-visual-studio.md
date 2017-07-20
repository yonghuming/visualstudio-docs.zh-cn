---
title: "Visual Studio 中的安全性 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 7314921a9416184c4bd63312bd5a82cef4102ddd
ms.contentlocale: zh-cn
ms.lasthandoff: 05/30/2017

---
# Visual Studio 中的安全性
<a id="security-in-visual-studio" class="xliff"></a>
你应该考虑应用程序开发的所有环节（从设计到部署）的安全性。 从尽可能安全地运行 Visual Studio 开始。 请参阅[用户权限](../ide/user-permissions-and-visual-studio.md)。  
  
 若要高效地开发安全的应用程序，应对安全概念和开发所针对的平台的安全特性有基本的了解。 你还应对安全编码技术有所了解。  
  
## 了解安全性
<a id="understanding-security" class="xliff"></a>  
 [安全性](/dotnet/standard/security/index)  
 描述 .NET Framework 代码访问安全性、基于角色的安全性、安全策略和安全工具。  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877)（使用开发人员必知十大安全技巧保卫你的代码）  
 介绍你应注意的问题，以免危害你的数据或系统。  
  
## 安全编码
<a id="coding-for-security" class="xliff"></a>  
 导致安全漏洞的大多数编码错误都是由于开发人员在处理用户输入时所做的假定错误，或者是由于他们对开发平台了解不够充分。  
  
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)  
 提供对组件进行分类以解决安全性问题的准则。  
  
 [安全性最佳做法](/cpp/top/security-best-practices-for-cpp)  
 讨论缓冲区溢出并提供 Microsoft Visual C++ 安全检查功能（由 /GS 编译时标志提供）的全面介绍。

## 构建安全性
<a id="building-for-security" class="xliff"></a>  
 安全性也是生成过程中的一个重要考虑因素。  一些额外步骤可以提高所部署应用的安全性，并帮助防止未经授权的反向工程、欺骗或其他攻击。

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 说明如何设置和开始使用免费的 PreEmptive Protection - Dotfuscator Community Edition，以保护 .NET 程序集免受反向工程威胁和未经授权的使用（如未经授权的调试）。
  
 [管理程序集签名和清单签名](managing-assembly-and-manifest-signing.md)  
 讨论强名称签名，它可用于唯一标识软件组件，从而防止名称欺骗。
