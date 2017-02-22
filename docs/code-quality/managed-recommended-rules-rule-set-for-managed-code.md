---
title: "托管代码的“托管建议规则”规则集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 托管代码的“托管建议规则”规则集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用“Microsoft 托管建议规则”规则集聚焦托管代码中最关键的问题，包括潜在的安全漏洞、应用程序崩溃和其他重要的逻辑和设计错误。  在为项目创建的任何自定义规则集中都应加入此规则集。  
  
|规则|说明|  
|--------|--------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|那自己可支配领域类型应该是一次性的|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|正确声明事件处理程序|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|用AssemblyVersionAttribute标记组件|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|接口方法能由子类可调用|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|拥有本机资源的类型应该是一次性的|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|移动P\/Invokes 到 NativeMethods类|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隐藏基类方法|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|正确实现IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不提高在意外的位置异常|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|避免重复加速器|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|P \/ Invoke入口点应该存在|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|P\/Invokes应该是不可见|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自动布局类型不应该是COM可见|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P \/ Invoke后立即调用GetLastError|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM可见类型的基类型应该是COM可见|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM注册方法应该匹配|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|正确声明P\/Invokes|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空的终结|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|值类型字段应该是便携的|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P\/Invoke 声明应为可移植声明|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|不要锁定具有弱标识的对象|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|检查SQL查询的安全漏洞|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|指定封送处理的P \/ Invoke字符串参数|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|审查的声明性安全上的值类型|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指针应该是不可见|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|有保证的类型不应公开栏|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法的安全性应该是类型的一个超集|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA方法应该只调用APTCA方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA类型应该只延长APTCA基本类型|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要使用链接请求间接公开方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|重写的链接请求应与基相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|裹在外层的try脆弱的finally子句|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|类型链接请求需要继承要求|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全关键类型可能不参与类型等价|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|默认构造函数必须至少与基类型默认构造函数一样关键|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委托必须绑定到具有一致透明度的方法|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|重写基方法时，方法必须保持一致的透明度|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透明方法必须只包含可验证的IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不得调用与SuppressUnmanagedCodeSecurity属性的方法|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明代码不得引用安全关键项|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不得满足LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|类型必须至少与其基类型和接口一样关键|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明方法不得使用安全断言|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不能调用本地代码|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|重新抛出保存堆栈的详细信息|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次释放对象|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|以内联方式初始化值类型的静态字段|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不要使用 WebMethod 标记服务组件|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|应释放可释放的字段|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|不要调用构造函数重写的方法|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可释放类型应声明终结器|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|终结器应调用基类的终结器|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|实现序列化构造函数|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|重写 ValueType.Equals 时应重载相等运算符|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|使用 STAThread 标记 Windows 窗体的入口点|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|标记所有不可序列化的字段|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|对 ISerializable 的类调用基类方法|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|以 SerializableAttribute 标记 ISerializable 类型|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|正确实现序列化方法|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|正确实现 ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|为格式化方法提供正确的参数|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|正确测试NaN|