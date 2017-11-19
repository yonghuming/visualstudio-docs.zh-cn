---
title: "CA1501： 避免过度继承 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c09a3367985613072944c5f74f0c708a149da15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501：避免过度继承
|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|类别|Microsoft.Maintainability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 类型在继承层次结构中的深度超过四级。  
  
## <a name="rule-description"></a>规则说明  
 深度嵌套的类型层次结构可能很难遵循、理解和维护。 此规则将限制到同一模块中的层次结构的分析。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请从继承层次结构中较浅的基类型派生该类型或消除一些中间的基类型。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告。 但是，代码可能会更加难以维护。 请注意，具体取决于基类型的可见性，解决违反此规则可能会创建重大更改。 例如，删除公共基类型是一项重大更改。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的类型。  
  
 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]