---
title: "CA1050： 声明命名空间中的类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c0aeaaf3531c45668b8804a6285be5df211c2754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050：在命名空间中声明类型
|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|类别|Microsoft.Design|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 公共或受保护的类型定义命名的命名空间的作用域之外。  
  
## <a name="rule-description"></a>规则说明  
 要防止名称冲突，命名空间中，另一种组织相关的类型对象层次结构中声明类型。 任何命名的命名空间之外的类型是不能在代码中引用的全局命名空间中。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请将类型放在一个命名空间。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 尽管你永远不需要禁止显示此规则的警告，则可以安全地执行此操作时将永远不会使用程序集，以及其他程序集。  
  
## <a name="example"></a>示例  
 下面的示例演示具有外部命名空间中，未正确声明类型的库和具有相同名称的命名空间中声明的类型。  
  
 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## <a name="example"></a>示例  
 下面的应用程序使用以前已定义的库。 请注意，在命名空间外声明的类型时，将创建名称`Test`不由命名空间限定。 另请注意，若要访问`Test`键入`Goodspace`，命名空间名称是必需的。  
  
 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]