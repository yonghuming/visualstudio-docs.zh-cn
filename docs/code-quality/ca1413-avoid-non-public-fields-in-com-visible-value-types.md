---
title: "CA1413： 避免在 COM 可见值类型中的非公共字段 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8dc7c435d9f853cfb67f7c45f5ec7116ff6fb8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413：避免在 COM 可见值类型中使用非公共字段
|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|类别|Microsoft.Interoperability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 专门标记为可见到组件对象模型 (COM) 的值类型声明的非公共实例字段。  
  
## <a name="rule-description"></a>规则说明  
 对 COM 可见的值类型的非公共实例字段对 COM 客户端可见。 检查的信息不应公开或将对设计或安全性意外的影响的字段的内容。  
  
 默认情况下，所有公共值类型都是对 COM 可见。 但是，若要减少误报，此规则要求要显式声明的类型的 COM 可见。 包含程序集都必须标记为<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>设置为`false`和类型都必须标记为<xref:System.Runtime.InteropServices.ComVisibleAttribute>设置为`true`。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，并保留隐藏的字段，请将值类型更改为引用类型或删除<xref:System.Runtime.InteropServices.ComVisibleAttribute>从类型的属性。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地公开的字段是可接受的情况下禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的类型。  
  
 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1407：避免在 COM 可见类型中使用静态成员](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)   
 [为互操作限定 .NET 类型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)