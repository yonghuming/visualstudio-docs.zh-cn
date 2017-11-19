---
title: "CA2103： 检查命令性安全 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6047df9ea1b5454d4c4c689a5baef887907779a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2103-review-imperative-security"></a>CA2103：检查命令性安全
|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|类别|Microsoft.Security|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 某个方法使用命令性安全，并且可能正在使用在要求处于活动状态时可以更改的状态信息或返回值来构造权限。  
  
## <a name="rule-description"></a>规则说明  
 命令性安全使用托管的对象来指定代码在执行期间，相比声明性安全，后者使用属性来存储在元数据中的权限和操作的权限和安全操作。 命令性安全是十分灵活，因为你可以设置的权限对象的状态并选择通过使用到运行时不可用的信息的安全操作。 合并到一起，灵活性得以实现，用于确定权限的状态不会保留的运行时信息保持不变，只要的操作是有效的风险。  
  
 应尽可能使用声明性安全。 声明性需求更易于了解。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 检查命令性安全请求，以确保权限的状态不依赖于正在使用权限可以更改的信息。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果权限不依赖于变化的数据。 但是，最好更改为其等效的声明性的强制性要求。  
  
## <a name="see-also"></a>另请参阅  
 [安全编码准则](/dotnet/standard/security/secure-coding-guidelines)   
 [数据和建模](/dotnet/framework/data/index)