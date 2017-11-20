---
title: "CA1016： 将程序集用 AssemblyVersionAttribute 标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 414a533e781be82cd0ffef1e9db234738ef07f16
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016：用 AssemblyVersionAttribute 标记程序集
|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|类别|Microsoft.Design|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 程序集没有版本号。  
  
## <a name="rule-description"></a>规则说明  
 程序集的标识组成的以下信息：  
  
-   程序集名称  
  
-   版本号  
  
-   区域性  
  
-   （对于强名称程序集） 的公钥。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 使用版本号唯一地标识程序集，并绑定到具有强名称的程序集中的类型。 版本号与版本和发行者策略一起使用。 默认情况下，仅使用用于生成应用程序的程序集版本运行应用程序。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，版本号的程序集使用添加<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>属性。 请参见以下示例。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不要禁止此规则的警告显示有关由第三方，或在生产环境中使用的程序集。  
  
## <a name="example"></a>示例  
 下面的示例演示具有的程序集<xref:System.Reflection.AssemblyVersionAttribute>应用的属性。  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [程序集版本控制](/dotnet/framework/app-domains/assembly-versioning)   
 [如何：创建发行者策略](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)