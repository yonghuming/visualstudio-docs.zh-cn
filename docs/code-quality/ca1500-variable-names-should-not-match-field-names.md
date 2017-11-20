---
title: "CA1500： 变量名不应与字段名 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7825078ff4d53ad5d90cdd8765f6f4120805b60f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500：变量名不应与字段名相同
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|类别|Microsoft.Maintainability|  
|是否重大更改|如果是针对作为字段具有相同名称的参数引发：<br /><br /> --否-如果外的程序集，而不考虑所做的更改都不可见的字段和声明参数的方法。<br />-中断性-如果你更改字段的名称，并可以程序集外可见。<br />-中断性-如果你更改参数的名称和声明它的方法可以程序集外可见。<br /><br /> 为字段具有相同名称的本地变量上激发时：<br /><br /> --否-如果外的程序集，而不考虑所做的更改都不可见字段。<br />--否-如果你更改本地变量的名称，不会更改字段的名称。<br />-间断-如果你更改字段的名称并且它可以程序集外可见。|  
  
## <a name="cause"></a>原因  
 实例方法声明的参数或其名称与声明类型的实例字段匹配的本地变量。 若要捕获与该规则冲突的本地变量，测试的程序集必须使用调试信息生成和关联的程序数据库 (.pdb) 文件必须可用。  
  
## <a name="rule-description"></a>规则说明  
 当某一实例字段的名称匹配的参数或局部变量的名称时，通过使用访问实例字段`this`(`Me`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 的方法主体内的关键字。 当维护代码，很容易忘记了这种差异，假定参数/本地变量引用实例字段，这会导致错误。 这是 true 尤其是对于较长的方法体。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，重命名参数/变量或字段。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示两个冲突的规则的情况。  
  
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]