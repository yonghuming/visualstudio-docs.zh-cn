---
title: "CA1903： 使用仅目标框架中的 API |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7caff553adfd812e671a2d8643b2352d9868ca43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903：仅使用目标框架中的 API
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|CheckId|CA1903|  
|类别|Microsoft.Portability|  
|是否重大更改|是-如果引发对该签名的外部可见成员或类型。<br /><br /> 非重大更改的方法的正文中激发时。|  
  
## <a name="cause"></a>原因  
 成员或类型使用一个成员或未包含与项目的目标框架的 service pack 中引入的类型。  
  
## <a name="rule-description"></a>规则说明  
 新成员和类型均包含在.NET Framework 2.0 Service Pack 1 和 2，.NET Framework 3.0 Service Pack 1 和 2 和.NET Framework 3.5 Service Pack 1。 面向.NET Framework 的主要版本的项目可能会无意中需要依赖这些新的 Api。 若要防止此依赖关系，将引发此规则上的任何新的成员和类型不包含默认情况下，与项目的目标框架的用法。  
  
 **目标框架和服务包依赖关系**  
  
|||  
|-|-|  
|目标框架时|在中引入的成员的用法激发|  
|.NET Framework 2.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET framework 2.0 SP1、.NET Framework 2.0 SP2、.NET Framework 3.0 SP1、.NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|不可用|  
  
 若要更改项目的目标框架，请参阅[面向特定的.NET Framework 版本](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要删除的服务包的依赖，删除所有使用新成员或类型的实例。 如果这是有意的依赖项，则禁止显示警告，或关闭此规则。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果这不是故意依赖于指定的服务包不禁止显示此规则的警告。 在此情况下，你的应用程序可能无法在系统上运行不带安装此 service pack。 禁止显示警告，或如果这是有意的依赖项关闭此规则。  
  
## <a name="example"></a>示例  
 下面的示例演示使用类型选项仅适用于.NET 2.0 Service Pack 1 的 DateTimeOffset 的类。 此示例需要的项目属性中的目标框架下拉列表中已选择了.NET Framework 2.0。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例通过将替换为 DateTime 类型的 DateTimeOffset 类型用法修复了前面所述的冲突。  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [可移植性警告](../code-quality/portability-warnings.md)   
 [面向特定的 .NET Framework 版本](../ide/targeting-a-specific-dotnet-framework-version.md)