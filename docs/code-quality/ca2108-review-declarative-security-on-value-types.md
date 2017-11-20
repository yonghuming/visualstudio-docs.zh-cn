---
title: "CA2108： 检查有关值类型的声明性安全 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a2d7ecd899b4da51e6ff200f1e18b00366db6669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108：检查有关值类型的声明性安全
|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|类别|Microsoft.Security|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 公共或受保护值类型受[数据和建模](/dotnet/framework/data/index)或[链接需求](/dotnet/framework/misc/link-demands)。  
  
## <a name="rule-description"></a>规则说明  
 值类型是分配和之前执行其他构造函数通过其默认构造函数初始化。 如果值类型受需或 LinkDemand，并且调用方没有权限而不满足的安全检查，任何构造函数的默认值将失败，并且将会引发安全异常。 未释放的值类型;它会保留在其默认构造函数设置的状态。 不要假定传递值类型的实例调用方有权创建或访问该实例。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 不能解决与此规则的冲突，除非从类型，删除的安全检查和使用方法级别的安全检查在其位置。 请注意，这种方式解决了冲突不会阻止从获取值类型的实例的权限不足的调用方。 你必须确保实例的值类型，在其默认状态下，未公开敏感信息，并且不能在有害的方式。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果任何调用方可以获得在其默认状态的值类型的实例，而不会造成安全风险，可以禁止显示此规则的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示包含违反此规则的值类型的库。 请注意，`StructureManager`类型假定传递值类型的实例调用方有权创建或访问该实例。  
  
 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## <a name="example"></a>示例  
 以下应用程序演示库的漏洞。  
  
 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 本示例生成以下输出。  
  
 **结构自定义构造函数： 请求失败。**  
**新值 SecuredTypeStructure 100 100**  
**新值 SecuredTypeStructure 200 200**   
## <a name="see-also"></a>另请参阅  
 [链接需求](/dotnet/framework/misc/link-demands)   
 [数据和建模](/dotnet/framework/data/index)