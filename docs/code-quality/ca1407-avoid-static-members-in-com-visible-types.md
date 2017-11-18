---
title: "CA1407： 避免在 COM 可见类型中的静态成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 43240b8969026a8bbec18528230d3ca97bcb2236
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407：避免在 COM 可见类型中使用静态成员
|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|类别|Microsoft.Interoperability|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 专门标记为到组件对象模型 (COM) 可见类型包含`public``static`方法。  
  
## <a name="rule-description"></a>规则说明  
 COM 不支持`static`方法。  
  
 属性和事件访问器、 运算符重载方法或通过使用标记的方法，将忽略此规则<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>属性或<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>属性。  
  
 默认情况下，以下是对 COM 可见： 程序集、 公共类型，公共类型中的公共实例成员和公共值类型的所有成员。  
  
 此规则发生，程序集级别<xref:System.Runtime.InteropServices.ComVisibleAttribute>必须设置为`false`和类-<xref:System.Runtime.InteropServices.ComVisibleAttribute>必须设置为`true`，如下面的代码所示。  
  
```csharp  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，更改设计，以使用提供的相同功能的实例方法`static`方法。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告，如果 COM 客户端不需要访问由提供的功能`static`方法。  
  
## <a name="example-violation"></a>冲突的示例  
  
### <a name="description"></a>描述  
 下面的示例演示`static`违反此规则的方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>注释  
 在此示例中， **Book.FromPages**不能调用方法，从 com。  
  
## <a name="example-fix"></a>解决冲突的示例  
  
### <a name="description"></a>描述  
 若要在前面的示例解决了冲突，无法更改的方法实例方法，但这样做不意义上此实例中。 更好的解决方案，将显式应用`ComVisible(false)`到此方法使它清楚地了解其他开发人员，该方法无法查看从 com。  
  
 下面的示例应用<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>到方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>相关的规则  
 [CA1017：用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406：避免对 Visual Basic 6 客户端使用 Int64 参数](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413：避免在 COM 可见值类型中使用非公共字段](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>另请参阅  
 [与非托管代码交互操作](/dotnet/framework/interop/index)