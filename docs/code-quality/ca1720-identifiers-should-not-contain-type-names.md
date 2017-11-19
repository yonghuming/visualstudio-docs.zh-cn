---
title: "CA1720： 标识符不应包含类型名称 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5418bc8d265c32057911df2d3a15aaddacf1398e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720：标识符不应包含类型名称
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|CheckId|CA1720|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 外部可见成员中的参数的名称包含一个数据类型名称。  
  
 - 或 -  
  
 外部可见成员的名称包含特定于语言的数据类型名称。  
  
## <a name="rule-description"></a>规则说明  
 参数和成员的名称更好地用于传达它们的含义来说明它们需要由开发工具提供的类型。 对于成员的名称，如果必须使用一个数据类型名称，则使用而不是特定于语言的一个独立于语言的名称。 例如，而不是 C# 类型名称 int，使用独立于语言的数据类型名称，Int32。  
  
 对照以下特定于语言的数据类型名称，不区分大小写的方式，检查每个离散令牌参数或成员的名称：  
  
-   Bool  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Int  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   无符号  
  
-   签名  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 此外，参数的名称还检查针对以下独立于语言的数据类型名称，不区分大小写方式：  
  
-   对象  
  
-   obj  
  
-   Boolean  
  
-   Char  
  
-   String  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   指针  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 **如果针对参数引发的：**  
  
 将替换为更好地说明了其含义的词或更通用术语，例如 'value' 参数的名称的数据类型标识符。  
  
 **如果激发针对成员：**  
  
 将替换术语，用于更好地描述它的含义、 独立于语言的同等或更通用术语，例如 value 成员的名称的语言特定的数据类型标识符。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 偶尔使用的基于类型的参数和成员名称可能正合适。 但是，对于新开发，没有已知会出现情况，则应该禁止显示此规则的警告。 对于以前发布的库，你可能需要禁止显示此规则的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1709：标识符的大小写应当正确](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：标识符不应包含下划线](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719：参数名不应与成员名冲突](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)