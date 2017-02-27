---
title: "按 ID 列出的性能规则 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a1c934c-4798-4df9-a8ef-eb17ef06b6a2
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 按 ID 列出的性能规则
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|警告|说明|  
|--------|--------|  
|[DA0001：使用 StringBuilder 进行串联](../Topic/DA0001:%20Use%20StringBuilder%20for%20concatenations.md)|对 System.String.Concat 的调用在分析数据中占很大比例。  请考虑使用 <xref:System.Text.StringBuilder> 类根据多个段构造字符串。|  
|[DA0002：缺少 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|探查器未能在分析运行期间找到 VSPerfCorProf.dll。  当使用命令行工具收集探查器数据，但未使用 VSPerfCLREnv.cmd 工具初始化必要的环境变量时，将出现此警告。|  
|[DA0003：大量内核样本](../profiling/da0003-many-kernel-samples.md)|为应用程序收集的很大一部分调用堆栈示例在内核模式下执行。  请考虑使用其他分析方法分析您的应用程序。|  
|[DA0004：处理器使用率很高](../profiling/da0004-high-processor-usage.md)|在使用检测方法收集的分析数据中，处理器 \(CPU\) 使用率相当高。  在分析受 CPU 限制的应用程序时，请考虑使用采样分析方法。|  
|[DA0005：频繁进行 GC2 收集](../profiling/da0005-frequent-gc2-collections.md)|在第 2 代垃圾回收中正在回收大量 .NET 内存对象。|  
|[DA0006：重写值类型的 Equals\(\)](../profiling/da0006-override-equals-parens-for-value-types.md)|对 Equals 方法或公共值类型的相等运算符的调用在分析数据中占很大比例。  请考虑实施更有效的方法。|  
|[DA0007：避免使用控制流异常](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|分析数据中 .NET Framework 异常处理程序的调用率高。  请考虑使用其他控制流逻辑来减少引发的异常数。|  
|[DA0008：收集的样本过少](../profiling/da0008-few-samples-collected.md)|分析运行期间仅收集了少量样本。  请考虑延长运行时间或加快采样速度，以获取更多重要结果。|  
|[DA0009: High % time in JIT](http://msdn.microsoft.com/zh-cn/b60c1767-515c-41d9-81c2-c70d0b7024fd)|实时 \(JIT\) 编译器中所用的时间占应用程序执行时间的百分比很大。|  
|[DA0010：高开销 GetHashCode](../profiling/da0010-expensive-gethashcode.md)|对该类型的 GetHashCode 方法的调用在分析数据中占很大比例或此方法分配内存。|  
|[DA0011：高开销的 CompareTo](../profiling/da0011-expensive-compareto.md)|类型的 CompareTo 方法开销巨大或分配内存。|  
|[DA0012：大量反射](../Topic/DA0012:%20Significant%20amount%20of%20Reflection.md)|对 System.Reflection 方法（如 InvokeMember 和 GetMember）或 Type 方法（如 MemberInvoke）的调用在分析数据中占很大比例。  如果可以，请考虑用对依赖程序集的方法的早期绑定替代这些方法。|  
|[DA0013：String.Split 或 String.Substring 的使用率高](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|对 System.String.Split 或 System.String.Substring 方法的调用在分析数据中占很大比例。  如果要测试字符串中是否存在子字符串，请考虑使用 System.String.IndexOf 或 System.String.IndexOfAny。|  
|[DA0014：以分页方式将活动内存移到磁盘的发生率极高](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|在分析运行中收集的系统性能数据表明，在整个分析运行期间将活动内存分页到磁盘以及从磁盘分页活动内存的发生率非常高。  这一级别的分页比率通常会影响应用程序的性能和响应速度。  请考虑通过修改算法来减少内存分配。  还可能需考虑应用程序的内存要求。在拥有更多内存的计算机上重新运行分析。|  
|[DA0017：以分页方式将活动内存移到磁盘的发生率高](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|在分析运行中收集的系统性能数据表明，在整个分析运行期间以分页方式将活动内存移到磁盘以及从磁盘移动活动内存的发生率高。  这一级别的分页比率通常会影响应用程序的性能和响应速度。  请考虑通过修改算法来减少内存分配。  还可能需考虑应用程序的内存要求。在拥有更多内存的计算机上重新运行分析。|  
|[DA0018：运行的 32 位应用程序达到了进程托管内存的限制](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|分析运行期间收集的系统数据表明，.NET Framework 内存堆已接近托管堆在 32 位进程中可以达到的最大大小。  报告的值是已分析进程处于活动状态时堆的最大观测值。  请考虑优化应用程序对托管资源的使用。|  
|[DA0021: 第 1 代垃圾回收的速率很高](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|分析期间收集的系统性能数据表明，与第 0 代数据收集相比，第 1 代垃圾回收中回收了 .NET Framework 对象的很大一部分内存。|  
|[DA0022: 第 2 代垃圾回收的速率很高](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|分析期间收集的系统性能数据表明，与第 0 代和第 1 代垃圾回收相比，第 2 代垃圾回收中回收了 .NET Framework 对象的很大一部分内存。|  
|[DA0023：垃圾回收占用的 CPU 时间很多](../profiling/da0023-high-gc-cpu-time.md)|分析期间收集的系统性能数据表明，与应用程序总处理时间相比，垃圾回收所用时间很长。|  
|[DA0024：垃圾回收占用的 CPU 时间过多](../profiling/da0024-excessive-gc-cpu-time.md)|分析期间收集的系统性能数据表明，与应用程序总处理时间相比，垃圾回收所用时间过长。|  
|[DA0026：处理过程的内核 CPU 时间过长](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|在内核模式下执行所用的那部分 CPU 时间超出了在用户模式下执行所用的时间。  请考虑重新进行分析并对系统调用 \(syscalls\) 数采样，以确定内核模式执行时间长的原因。|  
|[DA0029：不支持的 CLR 版本](../profiling/da0029-unsupported-clr-version.md)|您尝试分析的应用程序使用不受分析工具支持的 .NET Framework 1.1 版。|  
|[DA0030：收集数据库项目的层交互测量值](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|对 <xref:System.Data> 方法的调用在分析数据中占很大比例，并且您未收集分析运行中的层交互数据。  请考虑重新进行分析并添加层交互数据。|  
|[DA0038：锁争用率很高](../profiling/da0038-high-rate-of-lock-contentions.md)|随分析数据一起收集的系统性能数据表明应用程序执行期间锁争用的发生率很高。  请考虑使用并发分析方法重新进行分析，以找出争用的原因。|  
|[DA0039：锁争用率非常高](../profiling/da0039-very-high-rate-of-lock-contentions.md)|随分析数据一起收集的系统性能数据表明，应用程序执行期间锁争用的发生率过高。  请考虑使用并发分析方法重新进行分析，以找出争用的原因。|  
|[DA0501：所分析的进程的平均 CPU 使用率。](../Topic/DA0501:%20Average%20CPU%20consumption%20by%20the%20Process%20being%20profiled..md)|此消息报告处理器忙于执行应用程序指令所用的时间的百分比。  报告的值是对所有测量时间间隔求得的平均值，在这些时间间隔中正在分析的进程处于活动状态。  在具有多个处理器的计算机上，此值可以大于 100%。|  
|[DA0502：所分析的进程的 CPU 最大消耗量](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|此消息报告处理器忙于执行应用程序指令所用的时间的最大百分比。  报告的值是所有测量时间间隔中报告的最大值，在这些时间间隔中，正在分析的进程处于活动状态。  在具有多个处理器的计算机上，此百分比可以大于 100%。|  
|[DA0503：所分析的进程的平均工作集\(以字节为单位\)](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|此消息报告进程当前使用的以字节（工作集）为单位的平均物理内存量。  进程工作集表示当前位于物理内存中的进程地址空间中的页。|  
|[DA0504：所分析的进程的最大工作集\(以字节为单位\)](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|此消息报告进程当前使用的以字节为单位的最大物理内存量。  进程工作集表示当前位于物理内存中的进程地址空间中的页。  此规则报告分析处于活动状态时进程工作集的最大值。|  
|[DA0505：为所分析进程分配的平均专用字节数](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|此消息报告进程当前已分配的以字节（专用字节）为单位的平均虚拟内存量。  专用字节表示由进程分配的虚拟内存位置，该虚拟内存位置仅可由运行在该进程中的线程访问。|  
|[DA0506：为所分析的进程分配的最大专用字节数](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|此消息报告进程当前已分配的以字节（专用字节）为单位的最大虚拟内存量。  专用字节表示由进程分配的虚拟内存位置，该虚拟内存位置仅可由运行在该进程中的线程访问。|