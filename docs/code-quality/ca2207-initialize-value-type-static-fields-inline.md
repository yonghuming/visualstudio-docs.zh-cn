---
title: "CA2207： 以内联方式初始化值类型的静态字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f22975ba591e4300e54a4bda01f3802b393ae59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207：以内联方式初始化值类型的静态字段
|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|类别|Microsoft.Usage|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 某值类型声明显式静态构造函数。  
  
## <a name="rule-description"></a>规则说明  
 当声明值类型时，它将进行默认初始化值类型的所有字段都设置为零，其中所有引用类型字段都都设置为`null`(`Nothing`在 Visual Basic 中)。 只能保证在实例构造函数之前运行了显式静态构造函数或调用静态成员的类型。 因此，而不会调用实例构造函数创建的类型，如果静态构造函数是不能确保运行。  
  
 如果所有静态数据是初始化的内联的并声明没有显式静态构造函数，C# 和 Visual Basic 编译器添加`beforefieldinit`标志设为 MSIL 类定义。 编译器还会添加包含静态初始化代码的私有静态构造函数。 此专用的静态构造函数是保证能运行，访问该类型的任何静态字段之前。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突时初始化所有静态数据它声明并移除静态构造函数。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1810：以内联方式初始化引用类型的静态字段](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)