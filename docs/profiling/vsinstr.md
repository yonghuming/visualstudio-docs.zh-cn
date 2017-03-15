---
title: "VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "性能工具, 检测"
  - "检测, VSInstr 工具"
  - "分析工具, VSInstr"
  - "命令行工具, 检测"
  - "命令行, 工具"
  - "VSInstr"
  - "VSInstr 工具"
  - "性能工具, VSInstr 工具"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSInstr 工具用于检测二进制文件。  它通过使用下面的语法进行调用：  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 下表描述 VSInstr 工具选项：  
  
|选项|说明|  
|--------|--------|  
|**Help** 或 **?**|显示帮助。|  
|**U**|将重定向的控制台输出写为 Unicode 格式。  它必须是指定的第一个选项。|  
|`@filename`|指定其中每行均包含一个命令选项的响应文件的名称。不使用引号。|  
|**OutputPath** `:path`|指定检测映像的目标目录。  如果没有指定输出路径，则通过在文件名后追加“Orig”重命名原始二进制文件，并保存在相同目录下，然后检测二进制文件的副本。|  
|**Exclude** `:funcspec`|指定将由探测从检测中排除的函数规范。  当函数中的分析探测插入导致不可预知的或不需要的结果时，它将十分有用。<br /><br /> 不要使用引用同一二进制文件中的函数的 **Exclude** 和 **Include** 选项。<br /><br /> 您可以用单独的 **Exclude** 选项指定多个函数规范。<br /><br /> `funcspec` 被定义为：<br /><br /> \[命名空间\<分隔符1\>\] \[类\<分隔符2\>\]函数<br /><br /> \<分隔符1\>在本机代码中为 `::` ，在托管代码中为`.`。<br /><br /> \<分隔符2\>始终为 `::`<br /><br /> 代码覆盖率支持 **Exclude**。<br /><br /> 支持通配符 \*。  例如，若要排除命名空间中的所有函数，请使用：<br /><br /> MyNamespace::\*<br /><br /> 可以使用 **VSInstr \/DumpFuncs** 列出指定的二进制文件中各函数的完整名称。|  
|**Include** `:funcspec`|指定二进制文件中要使用探测检测的函数规范。  二进制文件中的所有其他函数将不被检测。<br /><br /> 您可以用单独的 **Include** 选项指定多个函数规范。<br /><br /> 不要使用引用同一二进制文件中的函数的 **Include** 和 **Exclude** 选项。<br /><br /> 代码覆盖率不支持 **Include**。<br /><br /> `funcspec` 被定义为：<br /><br /> \[命名空间\<分隔符1\>\] \[类\<分隔符2\>\]函数<br /><br /> \<分隔符1\>在本机代码中为 `::` ，在托管代码中为`.`。<br /><br /> \<分隔符2\>始终为 `::`<br /><br /> 支持通配符 \*。  例如，若要包括命名空间中的所有函数，请使用：<br /><br /> MyNamespace::\*<br /><br /> 可以使用 **VSInstr \/DumpFuncs** 列出指定的二进制文件中各函数的完整名称。|  
|**DumpFuncs**|列出指定映像内的函数。  不执行检测。|  
|**ExcludeSmallFuncs**|从检测中排除小型函数（不执行任何函数调用的短函数）。  **ExcludeSmallFuncs** 选项可以减少检测开销，从而提高检测速度。<br /><br /> 排除小型函数也减少了 .vsp 文件的大小和分析所需的时间。|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|插入分析标记（用来确定报告中数据的界限的标识符），您可以用该标记在 .vsp 报告文件中标识数据范围的起始或结束位置。<br /><br /> **Before**  ``  \- 紧挨在目标函数入口的前面。<br /><br /> **After**  ``  \- 紧挨在目标函数出口的后面。<br /><br /> **Top**  ``  \- 紧挨在目标函数入口的后面。<br /><br /> **Bottom**  ``  \- 紧挨在目标函数中的每个返回的前面。<br /><br /> `funcname` \- 目标函数的名称<br /><br /> `Markid` \- 一个用作分析标记的标识符的正整数（长型）。|  
|**Coverage**|执行覆盖率检测。  它仅可与下列选项一起使用：**Verbose**、**OutputPath**、**Exclude** 和 **Logfile**。|  
|**Verbose**|**Verbose** 选项用于查看有关检测过程的详细信息。|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|取消显示所有或特定警告。<br /><br /> `Message Number` \- 警告编号。  如果省略了 `Message Number`，将禁止显示所有警告。<br /><br /> 有关详细信息，请参阅[VSInstr 警告](../profiling/vsinstr-warnings.md)。|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|指定下列 VSInstr 数据收集控制选项的分析级别：<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  ``  \- 指定线程级别的数据收集控制函数。  只为当前线程启动或停止分析。  其他线程的分析状态不受影响。  默认值为线程。<br /><br /> **Process**  ``  \- 指定进程级别的分析数据收集控制函数。  为当前进程中的所有线程启动或停止分析。  其他进程的分析状态不受影响。<br /><br /> **Global**  ``  \- 指定全局级别（跨进程）的数据收集控制函数。<br /><br /> 如果没有指定分析级别，将出错。|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|将数据收集限定为目标函数以及该函数调用的子函数。<br /><br /> **Inside**  ``  \- 将 StartProfile 函数插入紧跟在目标函数入口后面的位置。  将 StopProfile 函数插入到紧在目标函数中的每个返回的前面。<br /><br /> **Outside**  ``  \- 将 StartProfile 函数紧挨在目标函数的每个调用前面插入。  将 StopProfile 函数插入到紧在目标函数的每个调用的后面。<br /><br /> `funcname` \- 目标函数的名称。|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|将目标函数以及该函数调用的子函数排除在数据收集范围之外。<br /><br /> **Inside**  ``  \- 将 SuspendProfile 函数插入紧跟在目标函数入口后面的位置。  将 ResumeProfile 函数插入到紧在目标函数中的每个返回的前面。<br /><br /> **Outside**  ``  \- 将 SuspendProfile 函数紧挨在目标函数入口的前面插入。  将 ResumeProfile 函数插入到紧在目标函数的出口的后面。<br /><br /> `funcname` \- 目标函数的名称。<br /><br /> 如果目标函数包含 StartProfile 函数，则 SuspendProfile 函数插入在它前面。  如果目标函数包含 StopProfile 函数，则 ResumeProfile 函数插入在它后面。|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|在分析运行期间开始数据收集。  它在指定位置插入 StartProfile API 函数。<br /><br /> **Before**  ``  \- 紧挨在目标函数入口的前面。<br /><br /> **After**  ``  \- 紧挨在目标函数出口的后面。<br /><br /> **Top**  ``  \- 紧挨在目标函数入口的后面。<br /><br /> **Bottom**  ``  \- 紧挨在目标函数中的每个返回的前面。<br /><br /> `funcname` \- 目标函数的名称。|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|在分析运行期间中止数据收集。  它在指定位置插入 StopProfile 函数。<br /><br /> **Before**  ``  \- 紧挨在目标函数入口的前面。<br /><br /> **After**  ``  \- 紧挨在目标函数出口的后面。<br /><br /> **Top**  ``  \- 紧挨在目标函数入口的后面。<br /><br /> **Bottom**  ``  \- 紧挨在目标函数中的每个返回的前面。<br /><br /> `funcname` \- 目标函数的名称。|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|在分析运行期间中止数据收集。  它在指定位置插入 SuspendProfile API。<br /><br /> **Before**  ``  \- 紧挨在目标函数入口的前面。<br /><br /> **After**  ``  \- 紧挨在目标函数出口的后面。<br /><br /> **Top**  ``  \- 紧挨在目标函数入口的后面。<br /><br /> **Bottom**  ``  \- 紧挨在目标函数中的每个返回的前面。<br /><br /> `funcname` \- 目标函数的名称。<br /><br /> 如果目标函数包含 StartProfile 函数，则 SuspendProfile 函数插入在它前面。|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|在分析运行期间开始或继续数据收集。<br /><br /> 它通常用于在 **SuspendOnly** 选项停止分析以后启动分析。  它在指定位置插入 ResumeProfile API。<br /><br /> **Before**  ``  \- 紧挨在目标函数入口的前面。<br /><br /> **After**  ``  \- 紧挨在目标函数出口的后面。<br /><br /> **Top**  ``  \- 紧挨在目标函数入口的后面。<br /><br /> **Bottom**  ``  \- 紧挨在目标函数中的每个返回的前面。<br /><br /> `funcname` \- 目标函数的名称。<br /><br /> 如果目标函数包含 StopProfile 函数，则 ResumeProfile 函数插入在它后面。|  
  
## 请参阅  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [VSInstr 警告](../profiling/vsinstr-warnings.md)   
 [分析工具报告视图](../profiling/performance-report-views.md)