---
title: "性能警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.performancerules"
helpviewer_keywords: 
  - "警告, 性能"
  - "性能警告"
  - "性能, 警告"
  - "托管代码分析警告, 性能警告"
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# 性能警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

性能警告支持高性能库和应用程序。  
  
## 本节内容  
  
|规则|说明|  
|--------|--------|  
|[CA1800：避免进行不必要的强制转换](../code-quality/ca1800-do-not-cast-unnecessarily.md)|重复强制转换会降低性能，特别是在精简的迭代语句中执行强制转换时。|  
|[CA1801：检查未使用的参数](../Topic/CA1801:%20Review%20unused%20parameters.md)|方法签名包含一个没有在方法体中使用的参数。|  
|[CA1802：在合适的位置使用文本](../code-quality/ca1802-use-literals-where-appropriate.md)|某个字段被声明为 static 和 read\-only（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Shared 和 ReadOnly），并使用可在编译时计算的值初始化。  因为赋给目标字段的值可在编译时计算，所以，请将声明更改为 const（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Const）字段，以便该值在编译时（而非运行时）计算。|  
|[CA1804：移除未使用的局部变量](../code-quality/ca1804-remove-unused-locals.md)|未使用的局部变量和不必要的赋值会增加程序集的大小并降低性能。|  
|[CA1806：不要忽略方法结果](../code-quality/ca1806-do-not-ignore-method-results.md)|创建一个新对象，但从不使用该对象；或者调用会创建并返回一个新字符串的方法，但从不使用这个新字符串；或者组件对象模型 \(COM\) 或 P\/Invoke 方法返回一个从不使用的 HRESULT 或错误代码。|  
|[CA1809：避免过多的局部变量](../code-quality/ca1809-avoid-excessive-locals.md)|优化性能的常见方法是将值存储于处理器寄存器，而不是内存中，这称为“注册值”。若要提高所有的局部变量都能注册的机会，应将局部变量的数目限制在 64 个以内。|  
|[CA1810：以内联方式初始化引用类型的静态字段](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|当一个类型声明显式静态构造函数时，实时 \(JIT\) 编译器会向该类型的每个静态方法和实例构造函数中添加一项检查，以确保之前已调用该静态构造函数。  静态构造函数检查会降低性能。|  
|[CA1811：避免使用未调用的私有代码](../code-quality/ca1811-avoid-uncalled-private-code.md)|某个私有或内部（程序集级别）成员在程序集中没有调用方，既不是由公共语言运行时调用的，也不是由委托调用的。|  
|[CA1812：避免未实例化的内部类](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|程序集级别类型的实例不是由程序集中的代码创建的。|  
|[CA1813：避免使用未密封的特性](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 类库提供用于检索自定义特性的方法。  默认情况下，这些方法搜索特性继承层次结构。  通过密封特性，将无需搜索继承层次结构，且能够提高性能。|  
|[CA1814：与多维数组相比，首选使用交错的数组](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|交错数组是元素为数组的数组。  构成元素的数组可以是不同的大小，这样可以减少某些数据集浪费的空间。|  
|[CA1815：重写值类型上的 Equals 和相等运算符](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|对于值类型，Equals 的继承的实现使用反射库，并比较所有字段的内容。  反射需要消耗大量计算资源，可能没有必要比较每一个字段是否相等。  如果希望用户对实例进行比较或排序，或者希望用户将实例用作哈希表键，则值类型应实现 Equals。|  
|[CA1816：正确调用 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|作为 Dispose 的实现的某个方法未调用 GC.SuppressFinalize，或者不是 Dispose 的实现的某个方法调用了 GC.SuppressFinalize，或者某个方法调用了 GC.SuppressFinalize 并传递 this（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中是 Me）以外的某个值。|  
|[CA1819：属性不应返回数组](../code-quality/ca1819-properties-should-not-return-arrays.md)|即使属性是只读的，该属性返回的数组也不是写保护的。  若要使数组不会被更改，属性必须返回数组的副本。  通常，用户不能理解调用这种属性的负面性能影响。|  
|[CA1820：使用字符串长度测试是否有空字符串](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|使用 String.Length 属性或 String.IsNullOrEmpty 方法比较字符串要比使用 Equals 的速度快得多。|  
|[CA1821：移除空的终结器](../code-quality/ca1821-remove-empty-finalizers.md)|应尽可能避免终结器，因为跟踪对象生存期会产生额外的性能系统开销。  空的终结器只会徒增系统开销，而没有一点好处。|  
|[CA1822：将成员标记为 static](../Topic/CA1822:%20Mark%20members%20as%20static.md)|可以将不访问实例数据或不调用实例方法的成员标记为 static（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中为 Shared）。  在将这些方法标记为 static 之后，编译器将向这些成员发出非虚拟调用站点。  这会使性能敏感的代码的性能得到显著提高。|  
|[CA1823：避免未使用的私有字段](../code-quality/ca1823-avoid-unused-private-fields.md)|检测到程序集内有似乎未访问过的私有字段。|  
|[CA1824：用 NeutralResourcesLanguageAttribute 标记程序集](../Topic/CA1824:%20Mark%20assemblies%20with%20NeutralResourcesLanguageAttribute.md)|NeutralResourcesLanguage 特性通知 ResourceManager 用于显示程序集的非特定区域性资源的语言。  这将改进所加载的第一个资源的查找性能，并缩小工作集。|