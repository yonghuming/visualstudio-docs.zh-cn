---
title: "Ca2211： 非常量非常量字段不应是可见 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac9a04038ba1d80e8abba2efbbab19c9779c384a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211：非常量字段不应是可见的
|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|类别|Microsoft.Usage|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护的静态字段不是常数也不是只读的。  
  
## <a name="rule-description"></a>规则说明  
 不是常数也不是只读字段的静态字段不是线程安全的。 对此类字段的访问必须严格控制，并需要高级编程技术来同步对类对象的访问。 因为这些是技巧难以学习和 master，和测试此类对象又带来了其自己的挑战，静态字段最适合用于存储不会更改的数据。 此规则适用于库;应用程序不应公开任何字段。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将静态字段常量或只读的。 如果这是不可能，重新设计要使用替代机制，如管理的基础字段对线程安全的访问的线程安全属性的类型。 请注意，例如锁争用和死锁问题的性能和库的行为可能会影响。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果你正在开发应用程序，因此具有完全控制访问，其中包含静态字段的类型。 库设计器不应禁止显示此规则; 的警告使用非常量静态字段，可以使用库使开发人员难以正确使用。  
  
## <a name="example"></a>示例  
 下面的示例演示了违反此规则的类型。  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]