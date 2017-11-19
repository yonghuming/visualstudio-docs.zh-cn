---
title: "CA1812： 避免未实例化的内部类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f6344b5dca6df21cba4d9a747925a24fffe1025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812：避免未实例化的内部类
|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|CheckId|CA1812|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 程序集级别类型的实例不是由程序集中的代码创建的。  
  
## <a name="rule-description"></a>规则说明  
 此规则尝试进行查找到的类型的构造函数之一的调用，并且如果不找到任何调用将报告冲突。  
  
 此规则不能检查以下类型：  
  
-   值类型  
  
-   抽象类型  
  
-   枚举  
  
-   委托  
  
-   编译器发出数组类型  
  
-   类型不能实例化且定义了`static`(`Shared`在 Visual Basic 中) 仅方法。  
  
 如果将应用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>对所分析的程序集，此规则不会标记为任何构造函数上发生`internal`因为不能判断是否正在由另一个使用字段`friend`程序集。  
  
 即使你不能解决此限制在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]代码分析，外部独立 FxCop 将发生在内部构造函数上如果每个`friend`程序集都在分析中存在。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，删除类型或添加的代码与使用它。 如果类型仅包含静态方法，请将以下项之一添加到要阻止编译器发出默认公共实例构造函数的类型：  
  
-   私有构造函数的类型面向[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]1.0 和 1.1 版。  
  
-   `static` (`Shared`在 Visual Basic 中) 修饰符类型面向[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告。 我们建议您禁止显示此警告在以下情况：  
  
-   如通过反射后期绑定方法创建的类<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>。  
  
-   类是由运行时或 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 自动创建的。 例如，用于实现 <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> 或 <xref:System.Web.IHttpHandler?displayProperty=fullName> 的类。  
  
-   类是作为具有新的约束的泛型类型参数传递。 例如，下面的示例将引发此规则。  
  
    ```csharp  
    internal class MyClass  
    {     
        public DoSomething()     
        {  
        }  
    }   
    public class MyGeneric<T> where T : new()  
    {  
        public T Create()  
        {  
            return new T();     
        }  
    }  
    // [...]   
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();  
    mc.Create();  
    ```  
  
 在这些情况下，我们建议您禁止显示此警告。  
  
## <a name="related-rules"></a>相关的规则  
 [CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801：检查未使用的参数](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)