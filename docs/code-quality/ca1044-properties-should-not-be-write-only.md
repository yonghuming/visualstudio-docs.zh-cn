---
title: "CA1044： 属性不应是只写 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c81c76fc20262d781e89e8ec786f7a640f6ee026
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044：属性不应是只写的
|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护属性 set 访问器，但不具有 get 访问器。  
  
## <a name="rule-description"></a>规则说明  
 获取访问器提供对属性的读取访问权限和 set 访问器提供写入访问权限。 虽然可以接受且经常需要使用只读属性，但设计准则禁止使用只写属性。 这是因为允许用户设置一个值，然后禁止用户查看值未提供任何安全性。 而且，如果没有读访问，将无法查看共享对象的状态，使其用处受到限制。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，将添加到属性的 get 访问器。 或者，如果只写属性的行为有必要，请考虑将此属性转换为一种方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 强烈建议不禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 在下面的示例中，`BadClassWithWriteOnlyProperty`是只写属性的类型。 `GoodClassWithReadWriteProperty`包含更正后的代码。  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]