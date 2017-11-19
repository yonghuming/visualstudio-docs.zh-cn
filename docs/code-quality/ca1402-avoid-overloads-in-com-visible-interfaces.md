---
title: "CA1402： 避免在 COM 可见接口中的重载 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdba95f57b969173cdcbfecbb8c2d8bcbc298d32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402：避免在 COM 可见接口中进行重载
|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|类别|Microsoft.Interoperability|  
|是否重大更改|重大|  
  
## <a name="cause"></a>原因  
 组件对象模型 (COM) 可见的接口声明的重载方法。  
  
## <a name="rule-description"></a>规则说明  
 在向 COM 客户端公开重载的方法时，只有第一个方法重载保留其名称。 对于后续重载将唯一名称，名称后面追加下划线字符 _ 和一个整数，该重载的声明顺序对应方法。 例如，考虑以下方法。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 这些方法公开给 COM 客户端，如下所示。  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Visual Basic 6 COM 客户端不能实现接口方法的名称中使用下划线。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，请重命名的重载的方法，使名称是唯一的。 或者，使该接口不可见向 COM 通过更改到的可访问性`internal`(`Friend`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 或通过应用<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>属性设置为`false`。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示与该规则冲突的接口和满足该规则的接口。  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1413：避免在 COM 可见值类型中使用非公共字段](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407：避免在 COM 可见类型中使用静态成员](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)   
 [Long 数据类型](/dotnet/visual-basic/language-reference/data-types/long-data-type)