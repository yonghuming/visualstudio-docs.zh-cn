---
title: "CA1709： 标识符应采用正确的大小写 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9332359228d657e9155996443822a5d1c11ad01
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709：标识符的大小写应当正确
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|CheckId|CA1709|  
|类别|Microsoft.Naming|  
|是否重大更改|中断性-如果是针对程序集、 命名空间、 类型、 成员和参数引发。<br /><br /> 非重大的泛型类型参数上激发时。|  
  
## <a name="cause"></a>原因  
 标识符名称的大小写不正确。  
  
 \- 或 -  
  
 标识符名称包含两个字母缩略词和第二个字母为小写。  
  
 \- 或 -  
  
 标识符名称包含三个或多个大写字母的首字母的缩写。  
  
## <a name="rule-description"></a>规则说明  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
 按照约定，参数名使用 camel 大小写;命名空间、 类型和成员名称使用 Pascal 大小写。 中混合使用大小写的名称，第一个字母为小写，，并在名称中任何其他单词的第一个字母为大写。 混合使用大小写的名称的示例包括"packetSniffer"、"ioFile"和"fatalErrorCode"。 采用 Pascal 大小写的名称中的第一个字母都大写，并在名称中任何其他单词的第一个字母为大写。 采用 Pascal 大小写的名称的示例包括"PacketSniffer"、"IOFile"和"FatalErrorCode"。  
  
 此规则将名称拆分成几个单词根据大小写，并检查任何两个字母的词与常见的两个字母字，例如"中"或"我的"的列表。 如果未找到匹配项，word 被假定为缩写词。 此外，此规则假定它找到的名称包含在行中的使用四个大写字母，或者在名称末尾处的行中使用三个大写字母时首字母缩写词。  
  
 按照约定，两个字母首字母缩写词使用全大写字母和三个或多个字符的首字母缩写词使用 Pascal 大小写。 下面的示例使用此命名约定: 数据库、 CR、 注册会计师和 Ecma。 下面的示例违反约定: 'Io'、 'XML' 和 'DoD，以及用于 nonparameter 名称、 xp 和 cpl。  
  
 ID 是特殊情况，若要使此规则的冲突。 “Id”不是首字母缩略词，而是“identification”的缩写。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 更改名称，以便它正确的大小写。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此警告，如果你有自己的命名约定，或者如果标识符表示正确的名称，例如，一家公司或技术的名称。  
  
 你还可以添加特定条款、 缩写，以及首字母缩写词，则为代码分析自定义字典。 指定自定义字典中的条款不会导致违反此规则。 有关详细信息，请参阅[如何： 自定义代码分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>相关的规则  
 [CA1708：标识符不应仅以大小写进行区分](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)