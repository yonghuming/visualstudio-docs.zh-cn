---
title: "混合建议规则规则集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3186b5b-0149-4a75-826e-e3539e4e703f
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9602b5af2506daebe88aac8459ea9da9c9a6ae08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="mixed-recommended-rules-rule-set"></a>“混合建议规则”规则集
Microsoft 混合建议规则专注于支持公共语言运行时，包括潜在的安全漏洞、 应用程序崩溃和其他重要的逻辑和设计错误在 c + + 项目中的最常见和关键问题。 应包括在任何自定义规则集中设置为 c + + 项目支持公共语言运行时创建此规则。 此规则集被设计与 Visual Studio 专业版和更高版本进行配置。  
  
|规则|说明|  
|----------|-----------------|  
|[C6001](../code-quality/c6001.md)|使用未初始化的内存|  
|[C6011](../code-quality/c6011.md)|取消引用 Null 指针|  
|[C6029](../code-quality/c6029.md)|未选中的值的使用|  
|[C6031](../code-quality/c6031.md)|忽略的返回值|  
|[C6053](../code-quality/c6053.md)|来自调用的零终止|  
|[C6054](../code-quality/c6054.md)|零终止缺少|  
|[C6059](../code-quality/c6059.md)|不正确的串联|  
|[C6063](../code-quality/c6063.md)|缺少 Format 函数的字符串自变量|  
|[C6064](../code-quality/c6064.md)|缺少 Format 函数的整型自变量|  
|[C6066](../code-quality/c6066.md)|缺少 Format 函数的指针自变量|  
|[C6067](../code-quality/c6067.md)|缺少 Format 函数的字符串指针自变量|  
|[C6101](../code-quality/c6101.md)|返回未初始化的内存|  
|[C6200](../code-quality/c6200.md)|索引超出最大缓冲区大小|  
|[C6201](../code-quality/c6201.md)|索引超出最大堆栈缓冲区大小|  
|[C6214](../code-quality/c6214.md)|通过无效强制转换为布尔值的 HRESULT|  
|[C6215](../code-quality/c6215.md)|通过无效强制转换为 HRESULT BOOL|  
|[C6216](../code-quality/c6216.md)|无效编译器插入强制转换为 HRESULT BOOL|  
|[C6217](../code-quality/c6217.md)|使用 NOT 无效 HRESULT 测试|  
|[C6220](../code-quality/c6220.md)|为-1 的无效 HRESULT 比较|  
|[C6226](../code-quality/c6226.md)|为-1 的无效 HRESULT 分配|  
|[C6230](../code-quality/c6230.md)|无效的 HRESULT 用作布尔值|  
|[C6235](../code-quality/c6235.md)|逻辑非零常量-或|  
|[C6236](../code-quality/c6236.md)|逻辑-或使用非零常量|  
|[C6237](../code-quality/c6237.md)|与逻辑零-并且失去副作用|  
|[C6242](../code-quality/c6242.md)|强制本地展开|  
|[C6248](../code-quality/c6248.md)|创建 Null DACL|  
|[C6250](../code-quality/c6250.md)|未发布的地址描述符|  
|[C6255](../code-quality/c6255.md)|Alloca 的未受保护的使用|  
|[C6258](../code-quality/c6258.md)|使用终止线程|  
|[C6259](../code-quality/c6259.md)|死按位代码中的复原能力或有限交换机|  
|[C6260](../code-quality/c6260.md)|字节算术的使用|  
|[C6262](../code-quality/c6262.md)|过多的堆栈使用|  
|[C6263](../code-quality/c6263.md)|使用在循环中 Alloca|  
|[C6268](../code-quality/c6268.md)|强制转换中缺少括号|  
|[C6269](../code-quality/c6269.md)|指针取消引用忽略|  
|[C6270](../code-quality/c6270.md)|缺少 Format 函数的浮点型自变量|  
|[C6271](../code-quality/c6271.md)|Format 函数的额外自变量|  
|[C6272](../code-quality/c6272.md)|Format 函数的非浮点型自变量|  
|[C6273](../code-quality/c6273.md)|Format 函数的非整型参数|  
|[C6274](../code-quality/c6274.md)|Format 函数的非字符自变量|  
|[C6276](../code-quality/c6276.md)|无效字符串的强制转换|  
|[C6277](../code-quality/c6277.md)|无效 CreateProcess 的调用|  
|[C6278](../code-quality/c6278.md)|新数组的标量删除不匹配|  
|[C6279](../code-quality/c6279.md)|标量新数组删除不匹配|  
|[C6280](../code-quality/c6280.md)|内存分配解除分配不匹配|  
|[C6281](../code-quality/c6281.md)|按位关系优先级|  
|[C6282](../code-quality/c6282.md)|赋值会替换测试|  
|[C6283](../code-quality/c6283.md)|基元数组新的标量删除不匹配|  
|[C6284](../code-quality/c6284.md)|Format 函数的无效对象自变量|  
|[C6285](../code-quality/c6285.md)|逻辑-或常量|  
|[C6286](../code-quality/c6286.md)|非零逻辑-焦点或失去副作用|  
|[C6287](../code-quality/c6287.md)|冗余的测试|  
|[C6288](../code-quality/c6288.md)|通过逻辑相互包含的和为 False|  
|[C6289](../code-quality/c6289.md)|通过逻辑的互相排斥的或为 True|  
|[C6290](../code-quality/c6290.md)|逻辑非和按位与的优先级|  
|[C6291](../code-quality/c6291.md)|逻辑非和按位或的优先级|  
|[C6292](../code-quality/c6292.md)|循环计数向上从最大值|  
|[C6293](../code-quality/c6293.md)|循环进行倒计时从最小值|  
|[C6294](../code-quality/c6294.md)|永远不会执行循环体|  
|[C6295](../code-quality/c6295.md)|无限循环|  
|[C6296](../code-quality/c6296.md)|只能执行一次循环|  
|[C6297](../code-quality/c6297.md)|Shift 结果强制转换为更大的大小|  
|[C6299](../code-quality/c6299.md)|位域与布尔比较|  
|[C6302](../code-quality/c6302.md)|Format 函数的无效字符串自变量|  
|[C6303](../code-quality/c6303.md)|Format 函数的无效宽字符串自变量|  
|[C6305](../code-quality/c6305.md)|不匹配的大小和计数的使用|  
|[C6306](../code-quality/c6306.md)|不正确的变量自变量函数的调用|  
|[C6308](../code-quality/c6308.md)|Realloc 泄漏|  
|[C6310](../code-quality/c6310.md)|非法异常筛选器常量|  
|[C6312](../code-quality/c6312.md)|异常继续执行循环|  
|[C6314](../code-quality/c6314.md)|按位的或的优先级|  
|[C6317](../code-quality/c6317.md)|补不|  
|[C6318](../code-quality/c6318.md)|异常继续搜索|  
|[C6319](../code-quality/c6319.md)|忽略用逗号进行分隔|  
|[C6324](../code-quality/c6324.md)|而不是字符串比较的字符串复制|  
|[C6328](../code-quality/c6328.md)|可能的自变量类型不匹配|  
|[C6331](../code-quality/c6331.md)|VirtualFree 无效标志|  
|[C6332](../code-quality/c6332.md)|VirtualFree 无效参数|  
|[C6333](../code-quality/c6333.md)|VirtualFree 无效大小|  
|[C6335](../code-quality/c6335.md)|泄露进程句柄|  
|[C6381](../code-quality/c6381.md)|关闭信息丢失|  
|[C6383](../code-quality/c6383.md)|元素计数字节的计数缓冲区溢出|  
|[C6384](../code-quality/c6384.md)|指针大小除法|  
|[C6385](../code-quality/c6385.md)|读取溢出|  
|[C6386](../code-quality/c6386.md)|写入溢出|  
|[C6387](../code-quality/c6387.md)|无效的参数值|  
|[C6388](../code-quality/c6388.md)|无效的参数值|  
|[C6500](../code-quality/c6500.md)|无效的特性属性|  
|[C6501](../code-quality/c6501.md)|冲突的特性属性值|  
|[C6503](../code-quality/c6503.md)|引用不能为 Null|  
|[C6504](../code-quality/c6504.md)|在非指针参数中为 Null|  
|[C6505](../code-quality/c6505.md)|对 Void 类型使用 MustCheck 属性|  
|[C6506](../code-quality/c6506.md)|非指针参数或数组的缓冲区大小|  
|[C6507](http://msdn.microsoft.com/en-us/18f88cd1-d035-4403-a6a4-12dd0affcf21)|取消引用零处的 Null 不匹配|  
|[C6508](../code-quality/c6508.md)|常量缓冲区上的写入权限|  
|[C6509](../code-quality/c6509.md)|返回使用的前置条件|  
|[C6510](../code-quality/c6510.md)|在非指针参数中以 Null 结尾的参数|  
|[C6511](../code-quality/c6511.md)|MustCheck 属性必须为 Yes 或 No|  
|[C6513](../code-quality/c6513.md)|没有缓冲区大小的元素大小|  
|[C6514](../code-quality/c6514.md)|缓冲区大小超过数组大小|  
|[C6515](../code-quality/c6515.md)|非指针参数的缓冲区大小|  
|[C6516](../code-quality/c6516.md)|在特性上无属性|  
|[C6517](../code-quality/c6517.md)|有效的不可读缓冲区的大小|  
|[C6518](../code-quality/c6518.md)|不可写的缓冲区的可写入大小|  
|[C6519](http://msdn.microsoft.com/en-us/2b6326b0-0539-4d26-8fb1-720114933232)|无效的批注：“NeedsRelease”属性的值必须为 Yes 或 No|  
|[C6521](http://msdn.microsoft.com/en-us/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|取消引用无效大小的字符串|  
|[C6522](../code-quality/c6522.md)|无效大小的字符串类型|  
|[C6523](http://msdn.microsoft.com/en-us/11397a31-b224-46b0-afb7-d49ca576a3bb)|无效大小的字符串参数|  
|[C6525](../code-quality/c6525.md)|无效大小字符串的不可访问的位置|  
|[C6526](http://msdn.microsoft.com/en-us/59c590c7-0098-4166-a1ac-87f324596002)|无效大小的字符串缓冲区类型|  
|[C6527](../code-quality/c6527.md)|无效的批注：“NeedsRelease”属性可能不可用于 void 类型的值|  
|[C6530](../code-quality/c6530.md)|无法识别的格式字符串样式|  
|[C6540](../code-quality/c6540.md)|对该函数使用属性批注将使其现有的所有 __declspec 批注无效|  
|[C6551](../code-quality/c6551.md)|大小规范无效：表达式不可分析|  
|[C6552](../code-quality/c6552.md)|Deref= 或 Notref= 无效：表达式不可分析|  
|[C6701](../code-quality/c6701.md)|该值不是有效的 Yes/No/Maybe 值|  
|[C6702](../code-quality/c6702.md)|该值不是字符串值|  
|[C6703](../code-quality/c6703.md)|该值不是一个数字|  
|[C6704](../code-quality/c6704.md)|意外的批注表达式错误|  
|[C6705](../code-quality/c6705.md)|批注自变量的预期数量与批注自变量的实际数量不匹配|  
|[C6706](../code-quality/c6706.md)|批注的意外批注错误|  
|[C6995](../code-quality/c6995.md)|无法保存 XML 日志文件|  
|[C26100](../code-quality/c26100.md)|争用条件|  
|[C26101](../code-quality/c26101.md)|无法正确地使用互锁的操作|  
|[C26110](../code-quality/c26110.md)|调用方无法持有锁|  
|[C26111](../code-quality/c26111.md)|调用方无法释放锁|  
|[C26112](../code-quality/c26112.md)|调用方不能包含任何锁定|  
|[C26115](../code-quality/c26115.md)|无法释放锁|  
|[C26116](../code-quality/c26116.md)|若要获取或持有锁的失败|  
|[C26117](../code-quality/c26117.md)|释放 unheld 的锁|  
|[C26140](../code-quality/c26140.md)|并发 SAL 批注错误|  
|[C28020](../code-quality/c28020.md)|表达式不满足此调用|  
|[C28021](../code-quality/c28021.md)|批注的参数必须为指针型|  
|[C28022](../code-quality/c28022.md)|此函数在函数的类不匹配用于定义它 typedef 函数的类。|  
|[C28023](../code-quality/c28023.md)|正在分配或传递此函数应该拥有 _Function_class\_为至少一个此类批注|  
|[C28024](../code-quality/c28024.md)|分配给该函数指针是使用函数类，不包含函数的类列表中添加批注。|  
|[C28039](../code-quality/c28039.md)|实际参数的类型应精确匹配的类型|  
|[C28112](../code-quality/c28112.md)|始终必须通过互锁函数访问通过互锁函数访问这些变量。|  
|[C28113](../code-quality/c28113.md)|访问局部变量通过互锁函数|  
|[C28125](../code-quality/c28125.md)|必须从调用此函数，在一个 try / except 块|  
|[C28137](../code-quality/c28137.md)|变量自变量应改为 （文本） 常量|  
|[C28138](../code-quality/c28138.md)|应改用变量常量的参数。|  
|[C28159](../code-quality/c28159.md)|请考虑改为使用另一个函数。|  
|[C28160](../code-quality/c28160.md)|错误批注|  
|[C28163](../code-quality/c28163.md)|该函数应永远不会从调用在一个 try / except 块|  
|[C28164](../code-quality/c28164.md)|自变量被传递给需要指向的对象 （不指向指针的指针） 的指针的函数|  
|[C28182](../code-quality/c28182.md)|取消引用 NULL 指针。 该指针包含与另一指针相同的 NULL 值。|  
|[C28183](../code-quality/c28183.md)|自变量可以是一个值，而在指针中找到的值的副本|  
|[C28193](../code-quality/c28193.md)|变量持有一个值，必须检查|  
|[C28196](../code-quality/c28196.md)|不符合的要求。 （表达式不的计算结果为 true。）|  
|[C28202](../code-quality/c28202.md)|非法引用非静态成员|  
|[C28203](../code-quality/c28203.md)|对类成员的不明确的引用。|  
|[C28205](../code-quality/c28205.md)|在非法上下文中使用的 _Success\_ 或 _On_failure\_|  
|[C28206](../code-quality/c28206.md)|若左操作数指向结构，则使用“->”|  
|[C28207](../code-quality/c28207.md)|若左操作数是一个结构，则使用“.”|  
|[C28209](../code-quality/c28209.md)|符号声明具有冲突的声明|  
|[C28210](../code-quality/c28210.md)|__on_failure 上下文的批注不得位于显式的 pre 上下文中|  
|[C28211](../code-quality/c28211.md)|SAL_context 所需的静态上下文名称|  
|[C28212](../code-quality/c28212.md)|批注所需的指针表达式|  
|[C28213](../code-quality/c28213.md)|_Use_decl_annotations\_ 批注必须用于引用上一个声明，且不对其进行修改。|  
|[C28214](../code-quality/c28214.md)|特性参数的名称必须为 p1...p9|  
|[C28215](../code-quality/c28215.md)|不能将 typefix 应用于已包含 typefix 的参数|  
|[C28216](../code-quality/c28216.md)|checkReturn 批注仅应用于特定函数参数的后置条件。|  
|[C28217](../code-quality/c28217.md)|对于函数，批注的参数数目与在文件中找到的数目不匹配|  
|[C28218](../code-quality/c28218.md)|对于函数参数，批注的参数与在文件中找到的参数不匹配|  
|[C28219](../code-quality/c28219.md)|批注中的批注参数所需的枚举成员|  
|[C28220](../code-quality/c28220.md)|批注中的批注参数所需的整数表达式|  
|[C28221](../code-quality/c28221.md)|批注中的参数所需的字符串表达式|  
|[C28222](../code-quality/c28222.md)|批注所需的 __yes、\__no 或 \__maybe|  
|[C28223](../code-quality/c28223.md)|未找到批注和参数所需的标记/标识符|  
|[C28224](../code-quality/c28224.md)|批注需要参数|  
|[C28225](../code-quality/c28225.md)|未在批注中找到所需参数的正确数目|  
|[C28226](../code-quality/c28226.md)|批注也不能为 PrimOp（在当前声明中）|  
|[C28227](../code-quality/c28227.md)|批注也不能为 PrimOp（请参阅上一个声明）|  
|[C28228](../code-quality/c28228.md)|批注参数：在批注中不能使用类型|  
|[C28229](../code-quality/c28229.md)|批注不支持参数|  
|[C28230](../code-quality/c28230.md)|参数类型没有成员。|  
|[C28231](../code-quality/c28231.md)|批注仅在数组上有效|  
|[C28232](../code-quality/c28232.md)|pre、post 或 deref 不适用于任何批注|  
|[C28233](../code-quality/c28233.md)|pre、post 或 dere 适用于块|  
|[C28234](../code-quality/c28234.md)|__at 表达式不适用于当前函数|  
|[C28235](../code-quality/c28235.md)|函数无法作为批注单独存在|  
|[C28236](../code-quality/c28236.md)|批注无法在表达式中使用|  
|[C28237](../code-quality/c28237.md)|不再支持参数上的批注|  
|[C28238](../code-quality/c28238.md)|参数上的批注具有多个值：stringValue 和 longValue。 使用 paramn=xxx|  
|[C28239](../code-quality/c28239.md)|参数上的批注包含两个值 stringValue 或 longValue；paramn=xxx。 仅使用 paramn=xxx|  
|[C28240](../code-quality/c28240.md)|参数上的批注包含 param2，但不包含 param1|  
|[C28241](../code-quality/c28241.md)|未识别参数上的函数的批注|  
|[C28243](../code-quality/c28243.md)|参数上函数的批注需要的取消引用次数多于已批注的实际类型所允许的次数|  
|[C28244](../code-quality/c28244.md)|函数的批注有无法分析参数/外部批注|  
|[C28245](../code-quality/c28245.md)|函数的批注将在非成员函数上批注“this”|  
|[C28246](../code-quality/c28246.md)|函数的参数批注与参数的类型不匹配|  
|[C28250](../code-quality/c28250.md)|函数的批注不一致：上一实例发生错误。|  
|[C28251](../code-quality/c28251.md)|函数的批注不一致：该实例发生错误。|  
|[C28252](../code-quality/c28252.md)|函数的批注不一致：参数在此实例中包含另一个批注。|  
|[C28253](../code-quality/c28253.md)|函数的批注不一致：参数在此实例中包含另一个批注。|  
|[C28254](../code-quality/c28254.md)|批注中不支持 dynamic_cast<>()|  
|[C28262](../code-quality/c28262.md)|对于批注，在函数中找到了批注的语法错误|  
|[C28263](../code-quality/c28263.md)|在条件批注中找到内部批注的语法错误|  
|[C28264](http://msdn.microsoft.com/en-us/bf6ea983-a06e-4752-a042-747a7dbf338c)|结果列出了必须为常量的值。|  
|[C28267](../code-quality/c28267.md)|在函数中找到了批注的语法错误。|  
|[C28272](../code-quality/c28272.md)|在检查参数时，函数的批注与函数声明不一致|  
|[C28273](../code-quality/c28273.md)|对于函数，线索与函数声明不一致|  
|[C28275](../code-quality/c28275.md)|_Macro_value\_ 的参数值为 null|  
|[C28279](../code-quality/c28279.md)|对于符号，已找到“起始”符号，但没有匹配的“结束”符号|  
|[C28280](../code-quality/c28280.md)|对于符号，已找到“结束”符号，但没有匹配的“起始”符号|  
|[C28282](../code-quality/c28282.md)|格式字符串必须位于前置条件中|  
|[C28285](../code-quality/c28285.md)|对于函数，参数中存在语法错误|  
|[C28286](../code-quality/c28286.md)|对于函数，在其结尾附近出现语法错误|  
|[C28287](../code-quality/c28287.md)|对于函数，在 _At\_() 批注中出现语法错误（无法识别的参数名）|  
|[C28288](../code-quality/c28288.md)|对于函数，在 _At\_() 批注中出现语法错误（无效的参数名）|  
|[C28289](../code-quality/c28289.md)|对于函数：ReadableTo 或 WritableTo 没有用作参数的限制规范|  
|[C28290](../code-quality/c28290.md)|函数的批注包含的外部对象数量多于实际的参数数量|  
|[C28291](../code-quality/c28291.md)|deref 级别 0 处的 post null/notnull 对于函数无意义。|  
|[C28300](../code-quality/c28300.md)|运算符的不可兼容类型的表达式操作数|  
|[C28301](../code-quality/c28301.md)|函数的第一个声明中不包含任何批注。|  
|[C28302](../code-quality/c28302.md)|在批注中找到多余的 _Deref\_ 运算符。|  
|[C28303](../code-quality/c28303.md)|在批注中找到含义模糊的 _Deref\_ 运算符。|  
|[C28304](../code-quality/c28304.md)|发现未正确放置的 _Notref\_ 运算符被应用到令牌。|  
|[C28305](../code-quality/c28305.md)|在分析标记时发现错误。|  
|[C28306](../code-quality/c28306.md)|参数上的批注是退化|  
|[C28307](../code-quality/c28307.md)|参数上的批注是退化|  
|[C28350](../code-quality/c28350.md)|批注介绍了无条件适用的情形。|  
|[C28351](../code-quality/c28351.md)|批注介绍了在条件中无法使用动态值（变量）的位置。|  
|[CA1001 具有](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|具有可释放字段的类型应该是可释放的|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|正确声明事件处理程序|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|用 AssemblyVersionAttribute 标记程序集|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|接口方法应可由子类型调用|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|拥有本机资源的类型应是可释放的|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|将 P/Invoke 移动到 NativeMethods 类|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隐藏基类方法|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|正确实现 IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不要在意外的位置引发异常|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|避免快捷键重复|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke 入口点应该存在|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes 应该是不可见的|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自动布局类型不应对 COM 可见|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|紧接在 P/Invoke 之后调用 GetLastError|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可见类型的基类型应对 COM 可见|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|应对 COM 注册方法进行匹配|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|正确声明 P/Invoke|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空终结器|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|值类型字段应为可移植字段|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke 声明应为可移植声明|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|不要锁定具有弱标识的对象|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|检查 SQL 查询是否存在安全漏洞|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|指定对 P/Invoke 字符串自变量进行封送处理|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|检查有关值类型的声明性安全|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指针应为不可见|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保护的类型不应公开字段|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性应是类型安全性的超集|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 方法应只调用 APTCA 方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 类型应只扩展 APTCA 基类型|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要使用链接请求间接公开方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|重写链接请求应与基相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|在外部 try 块中包装易受攻击的 finally 子句|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|类型链接请求需要继承请求|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全关键类型不能参与类型等效|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|默认构造函数必须至少与基类型默认构造函数为关键|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委托必须绑定到具有一致透明度的方法|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|在重写基方法时，方法必须保持一致的透明度|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透明方法只能包含可验证的 IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不得调用具有 SuppressUnmanagedCodeSecurity 特性的方法|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明代码不得引用安全关键项|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不得满足 LinkDemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|类型必须是至少与其基类型和接口一样关键|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明方法不得使用安全断言|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不得调入本机代码|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|再次引发以保留堆栈详细信息|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次释放对象|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|以内联方式初始化值类型的静态字段|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不要使用 WebMethod 标记服务组件|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|应释放可释放的字段|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|不要在构造函数中调用可重写的方法|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可释放类型应声明终结器|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|终结器应调用基类的终结器|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|实现序列化构造函数|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|重写 ValueType.Equals 时应重载相等运算符|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|使用 STAThread 标记 Windows 窗体的入口点|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|标记所有不可序列化的字段|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|对 ISerializable 类型调用基类方法|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|用 SerializableAttribute 标记 ISerializable 类型|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|正确实现序列化方法|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|正确实现 ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|为格式化方法提供正确的自变量|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|正确测试 NaN|