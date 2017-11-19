---
title: "CA1303： 不要传递文本作为本地化的参数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce6ed64a6991342b4dc1506b8384f7691cc90b8f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303：不要将文本作为本地化参数传递
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 方法将字符串作为参数传递给构造函数或方法中的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]类库和字符串应该是可本地化。  
  
 文本字符串作为值传递给参数或属性和一个或多个以下情况下为 true 时，会引发此警告：  
  
-   <xref:System.ComponentModel.LocalizableAttribute>参数或属性的属性设置为 true。  
  
-   参数或属性名称包含"Text"、"消息"标题"。  
  
-   传递给 Console.Write 或 Console.WriteLine 方法将字符串参数的名称为"value"format"。  
  
## <a name="rule-description"></a>规则说明  
 在源代码中嵌入的字符串难以本地化。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，用替换字符串文本的字符串的实例通过检索<xref:System.Resources.ResourceManager>类。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果将未本地化代码库，或者如果字符串未公开到最终用户或使用代码库的开发人员。  
  
 用户可以消除干扰针对不应将传递本地化的字符串通过任一重命名的参数或属性名为，或通过将这些项作为条件标记的方法。  
  
## <a name="example"></a>示例  
 下面的示例演示当任何一个其两个自变量超出范围时引发异常的方法。 对于第一个参数，异常构造函数传递与该规则冲突的文字字符串。 对于第二个参数构造函数正确传递通过检索字符串<xref:System.Resources.ResourceManager>。  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [桌面应用中的资源](/dotnet/framework/resources/index)