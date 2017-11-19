---
title: "： ca1722 标识符应采用正确的前缀 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 84cf14fc28a3de1d6ff5bff9e40216953d5d1461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722：标识符应采用正确的前缀
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|类别|Microsoft.Naming|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 标识符具有不正确的前缀。  
  
## <a name="rule-description"></a>规则说明  
 按照约定，只有某些编程元素具有以特定前缀开头的名称。  
  
 类型名称并不一定特定前缀，不应以 C 作为前缀。 此规则报告类型名称，例如 CMyClass 的冲突，并不会报告作为类型名称，例如缓存的冲突。  
  
 命名约定提供了通用的外观的库，面向公共语言运行时。 这减少了学习曲线，才能使用新的软件库和客户更有信心库由在开发的托管代码中有专业技能的人员。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 删除从标识符前缀。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1715：标识符应具有正确的前缀](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)