---
title: "Visual Studio 中的安全性 | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: "20"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 25b0f76c657f4d4df7375b4fc9e418e8806bd51f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="security-in-visual-studio"></a>Visual Studio 中的安全性
你应该考虑应用程序开发的所有环节（从设计到部署）的安全性。 从尽可能安全地运行 Visual Studio 开始。 请参阅[用户权限](../ide/user-permissions-and-visual-studio.md)。  
  
 若要高效地开发安全的应用程序，应对安全概念和开发所针对的平台的安全特性有基本的了解。 你还应对安全编码技术有所了解。  
  
## <a name="understanding-security"></a>了解安全性  
 [安全性](/dotnet/standard/security/index)  
 描述 .NET Framework 代码访问安全性、基于角色的安全性、安全策略和安全工具。  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877)（使用开发人员必知十大安全技巧保卫你的代码）  
 介绍你应注意的问题，以免危害你的数据或系统。  
  
## <a name="coding-for-security"></a>安全编码  
 导致安全漏洞的大多数编码错误都是由于开发人员在处理用户输入时所做的假定错误，或者是由于他们对开发平台了解不够充分。  
  
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)  
 提供对组件进行分类以解决安全性问题的准则。  
  
 [安全性最佳做法](/cpp/top/security-best-practices-for-cpp)  
 讨论缓冲区溢出并提供 Microsoft Visual C++ 安全检查功能（由 /GS 编译时标志提供）的全面介绍。

## <a name="building-for-security"></a>构建安全性  
 安全性也是生成过程中的一个重要考虑因素。  一些额外步骤可以提高所部署应用的安全性，并帮助防止未经授权的反向工程、欺骗或其他攻击。

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 说明如何设置和开始使用免费的 PreEmptive Protection - Dotfuscator Community Edition，以保护 .NET 程序集免受反向工程威胁和未经授权的使用（如未经授权的调试）。
  
 [管理程序集签名和清单签名](managing-assembly-and-manifest-signing.md)  
 讨论强名称签名，它可用于唯一标识软件组件，从而防止名称欺骗。