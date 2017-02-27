---
title: "托管代码的“安全规则”规则集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 托管代码的“安全规则”规则集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您应加入“Microsoft 安全规则”规则集，以尽可能多地报告潜在的安全问题。  
  
|规则|说明|  
|--------|--------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|检查SQL查询的安全漏洞|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|在常规处理程序中捕捉非 CLSCompliant 异常|  
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|检查命令性安全|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|不要声明只读可变引用类型|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|数组字段不应为只读|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|保护断言|  
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|检查 deny 权限和 permit only 权限的使用情况|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|审查的声明性安全上的值类型|  
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|检查可见的事件处理程序|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指针应该是不可见|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|有保证的类型不应公开栏|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法的安全性应该是类型的一个超集|  
|[CA2115](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)|使用本机资源时调用 GC.KeepAlive|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA方法应该只调用APTCA方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA类型应该只延长APTCA基本类型|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|检查 SuppressUnmanagedCodeSecurityAttribute 用法|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|密封满足私有接口的方法|  
|[CA2120](../Topic/CA2120:%20Secure%20serialization%20constructors.md)|保护序列化构造函数|  
|[CA2121](../Topic/CA2121:%20Static%20constructors%20should%20be%20private.md)|静态构造函数应为私有|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要使用链接请求间接公开方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|重写的链接请求应与基相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|裹在外层的try脆弱的finally子句|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|类型链接请求需要继承要求|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|安全关键常量应是透明的|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全关键类型可能不参与类型等价|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|默认构造函数必须至少与基类型默认构造函数一样关键|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委托必须绑定到具有一致透明度的方法|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|重写基方法时，方法必须保持一致的透明度|  
|[CA2135](../Topic/CA2135:%20Level%202%20assemblies%20should%20not%20contain%20LinkDemands.md)|级别 2 程序集不应包含 LinkDemand|  
|[CA2136](../Topic/CA2136:%20Members%20should%20not%20have%20conflicting%20transparency%20annotations.md)|成员不应有相互冲突的透明度注释|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透明方法必须只包含可验证的IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不得调用与SuppressUnmanagedCodeSecurity属性的方法|  
|[CA2139](../Topic/CA2139:%20Transparent%20methods%20may%20not%20use%20the%20HandleProcessCorruptingExceptions%20attribute.md)|透明方法不能使用 HandleProcessCorruptingExceptions 特性|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明代码不得引用安全关键项|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不得满足LinkDemands|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|不应使用 LinkDemand 保护透明代码|  
|[CA2143](../Topic/CA2143:%20Transparent%20methods%20should%20not%20use%20security%20demands.md)|透明方法不应使用安全要求|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透明代码不应从字节数组加载程序集|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|不应使用 SuppressUnmanagedCodeSecurityAttribute 修饰透明方法|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|类型必须至少与其基类型和接口一样关键|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明方法不得使用安全断言|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不能调用本地代码|  
|[CA2210](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)|程序集应具有有效的强名称|