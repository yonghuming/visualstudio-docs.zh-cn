---
title: "托管代码的“基本设计准则规则”规则集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# 托管代码的“基本设计准则规则”规则集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用“Microsoft 基本设计准则规则”规则集侧重于使您的代码更易于理解和使用。  如果项目包括库代码或者如果要实施最佳做法以更易于维护代码，则应加入此规则集。  
  
 “基本设计准则规则”包括“Microsoft 最少量建议规则”规则集中的所有规则。  有关最少量规则的列表，请参见 [托管代码的“托管建议规则”规则集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)。  
  
 下表介绍了“Microsoft 基本设计准则规则”规则集中的所有规则。  
  
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
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|代表们必须绑定到具有一致透明度的方法|  
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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|不要在泛型类型中使用静态成员|  
|[CA1002](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|不要公开泛型列表|  
|[CA1003](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|使用泛型事件处理程序实例|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|泛型方法应提供类型参数|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|避免泛型类型的参数过多|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|不要将泛型类型嵌套在成员签名|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|使用泛型（如适用）|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|枚举应该具有0值|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|集合应实现泛型接口|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|考虑通过基类型作为参数|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|抽象类型应该不具有构造函数|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|重载加法方法和减法方法时重载相等运算符|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|集用CLSCompliantAttribute标记程序集|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|与请将ComVisibleAttribute标记程序集|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|用 AttributeUsageAttribute 标记特性|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|定义访问器的属性参数|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|索引不应该是多维的|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|使用属性（如适用）|  
|[CA1025](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|代替重复的参数与参数数组|  
|[CA1026](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|默认参数不应该被用|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|使用FlagsAttribute标记枚举|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|枚举应该是Int32类型|  
|[CA1030](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|使用事件（如适用）|  
|[CA1031](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|没有捕获一般的异常类型|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|实施标准异常构造|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|嵌套类型不应该是可见的|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection实现含有强类型成员|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|可比较类型重写方法|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|枚举器应该是强类型|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|列表是强类型|  
|[CA1041](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|提供ObsoleteAttribute消息|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|将整型或字符串参数用于索引器|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|属性不应是只写的|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|不要对引用类型重载相等运算符|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|不要在密封类型中声明受保护的成员|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|不要在密封类型声明虚拟成员|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|声明中的命名空间的类型|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|不要声明可见实例字段|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|静态成员的类型应密封|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|静态容器类型不应具有构造函数|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI参数不应为字符串|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI返回值不应是字符串|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI属性不应是字符串|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|字符串的URI重载调用的System.Uri重载|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|类型不应扩展某些基类型|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|成员不应公开某些具体类型|  
|[CA1064](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|异常应该是公共的|  
|[CA1500](../Topic/CA1500:%20Variable%20names%20should%20not%20match%20field%20names.md)|变量名不应与字段名匹配|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|避免过度复杂|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|标识符应超过大小写不同|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|标识符不应该匹配的关键字|  
|[CA1801](../Topic/CA1801:%20Review%20unused%20parameters.md)|审查未使用的参数|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|删除未使用的当地人|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|避免过多的当本地|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|初始化引用类型的静态字段|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|避免使用未调用的私有代码|  
|[CA1812](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|避免未实例内部类|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|避免未密封的属性|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|在多维交错数组更好|  
|[CA1815](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|重写equals和操作员的值类型等于|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|属性不应返回数组|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|测试使用字符串长度的空字符串|  
|[CA1822](../Topic/CA1822:%20Mark%20members%20as%20static.md)|将成员标记为 static|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|避免未使用的私有字段|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|不要引发保留的异常类型|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Win32 API的使用管理等同|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|正确的实例化参数异常|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非常数区域应该是不可见|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|不要使用FlagsAttribute标记枚举|  
|[CA2219](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|在异常子句中不引发异常|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|终结应受到保护|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|不要降低继承成员的可见性|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|成员应该超过返回类型不同|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|重写equals超载运算符等号|  
|[CA2225](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|运算符重载具有命名的备用项|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|运算符应有对称重载|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|集合属性应该是只读|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|使用PARAMS的可变参数|  
|[CA2234](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|传递System.Uri对象，而不是字符串|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|提供反序列化方法可选字段|