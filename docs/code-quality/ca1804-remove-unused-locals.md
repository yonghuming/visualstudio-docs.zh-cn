---
title: "CA1804： 移除未使用的局部变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9217f3109c6ef03de33e444e723caa585d065efb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1804-remove-unused-locals"></a>CA1804：移除未使用的局部变量
|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 一种方法声明本地变量，但不使用除变量可能为接收者的赋值语句。 通过此规则进行分析，必须使用调试信息生成测试的程序集和关联的程序数据库 (.pdb) 文件必须可用。  
  
## <a name="rule-description"></a>规则说明  
 未使用的局部变量和不必要的赋值会增加程序集的大小并降低性能。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除或使用本地变量。 请注意，C# 编译器，是附带[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]中删除未使用的局部变量时`optimize`启用选项。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果变量是编译器发出，禁止显示此规则的警告。 如果性能和代码维护不是优先考虑的因素，则也可以禁止显示此规则的警告或禁用规则，安全。  
  
## <a name="example"></a>示例  
 下面的示例演示几个未使用的本地变量。  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1809：避免过多的局部变量](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812：避免未实例化的内部类](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801：检查未使用的参数](../code-quality/ca1801-review-unused-parameters.md)