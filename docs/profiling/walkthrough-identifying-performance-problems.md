---
title: "演练：分析应用程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具, 演练"
  - "性能工具, 演练"
  - "性能, 分析"
  - "分析应用程序, 演练"
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 53
---
# 演练：分析应用程序
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此演练演示如何分析应用程序来识别性能问题。  
  
 在本演练中，您将逐步完成分析托管应用程序的过程，使用采样和检测来确定并识别应用程序中的性能问题。  
  
 在本演练中，您将执行以下步骤：  
  
-   通过使用取样方法分析应用程序。  
  
-   分析取样分析结果，找出并解决性能问题。  
  
-   通过使用检测方法分析应用程序。  
  
-   分析检测分析结果，找出并解决性能问题。  
  
## 系统必备  
  
-   C\# 的理解程度为中等。  
  
-   [PeopleTrax 示例](../profiling/peopletrax-sample-profiling-tools.md) 的副本。  
  
 若要使用分析提供的信息，最好有调试符号信息。  
  
## 使用采样方法分析  
 取样是一种分析方法，它定期对相关进程进行轮询，以确定活动函数。  所得数据提供当对进程进行取样时相关函数位于调用堆栈顶部的频率的计数。  
  
#### 通过使用取样方法分析应用程序  
  
1.  使用管理员特权打开 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]。  需要以管理员身份运行才能进行分析。  
  
2.  打开 PeopleTrax 解决方案。  
  
     PeopleTrax 解决方案现在出现在解决方案资源管理器中。  
  
3.  将项目配置设置设为**“发布”**。  
  
     应该使用发行版本来检测应用程序中的性能问题。  建议使用发行版本进行分析的原因是调试版本将附加信息编译到其中，这可能对性能产生负面影响，从而无法准确演示性能问题。  
  
4.  在**“分析”**菜单上，单击**“启动性能向导”**。  
  
     将出现性能向导。  
  
5.  确保选中**“CPU 采样\(建议\)”**，然后单击**“下一步”**。  
  
6.  在**“要以哪个应用程序为目标进行分析”**中，选择“PeopleTrax”，然后单击**“下一步”**。  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 将生成项目并开始分析应用程序。  将出现**“PeopleTrax”**应用程序窗口。  
  
7.  单击**“获取 People”**。  
  
8.  单击**“导出数据”**。  
  
     将打开“记事本”并显示一个包含从**“PeopleTrax”**导出的数据的新文件。  
  
9. 关闭“记事本”，然后关闭**“PeopleTrax”**应用程序。  
  
     探查器将生成分析数据 \(\*.vsp\) 文件，在性能资源管理器窗口的“报告”部分列出文件名，并在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 主窗口自动加载数据文件的**“摘要”**视图。  
  
#### 分析取样分析结果  
  
1.  “摘要”视图将显示以下内容：分析运行过程中 CPU 利用率的时间线、**“热路径”**列表（表示最活跃的应用程序调用树的分支），以及**“执行单个工作最多的函数”**列表（显示在其自身的函数体中执行代码时采样最多的函数）。  
  
     检查**“热路径”**列表，请注意 PeopleNS.People.GetNames 方法是最靠近列表结尾的 PeopleTrax 函数。  其位置使其非常适于分析。  单击函数名称可在**“函数详细信息”**视图中显示 GetNames 的详细信息。  
  
2.  **“函数详细信息”**视图包含两个窗口。  开销分布窗口提供函数所执行工作的图形视图、该函数所调用的函数执行的工作，以及调用该函数的函数在采样实例数中所占的份额。  通过单击函数名称可更改作为视图焦点的函数。  例如，可单击 PeopleNS.People.GetPeople 使 GetPeople 成为所选函数。  
  
     **“函数代码视图”**窗口显示函数的源代码（如果可用），并突出显示所选函数中开销最大的行。  如果选择 GetNames，则可以发现此函数从应用程序资源中读取字符串，然后使用 <xref:System.IO.StringReader> 将字符串中的每一行添加到 <xref:System.Collections.ArrayList>。  没有一种显而易见的方法来优化此函数。  
  
3.  由于 PeopleNS.People.GetPeople 是 GetNames 的唯一调用方，因此在开销分布窗口中单击 GetPeople 可检查其代码。  此方法从 GetNames 生成的人员和公司的名称中返回 PersonInformationNS.PersonInformation 对象的 <xref:System.Collections.ArrayList>。  但是，每次创建 PersonInformation 对象时，都将调用 GetNames 两次。  可以发现，通过在方法的开始位置仅创建一次列表，并在 PersonInformation 创建循环过程中对这些列表编制索引，可以轻松优化此方法。  
  
4.  GetPeople 的备选版本随示例应用程序代码一起提供，您可以通过将条件编译符号添加到生成属性来调用优化的函数。  在解决方案资源管理器窗口中，右击 People 项目，然后单击**“属性”**。  在属性页菜单上单击**“生成”**，然后在“条件编辑符号”文本框中键入 **OPTIMIZED\_GETPEOPLE**。  GetPeople 的优化版本将在下一个版本中取代原始方法。  
  
5.  重新运行性能会话。  在性能资源管理器工具栏上，单击**“启动并启用分析功能”**。  单击**“GetPeople”**，然后单击**“导出数据”**。  关闭出现的记事本窗口，然后关闭 People Trax 应用程序。  
  
     将生成新的分析数据文件，并在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 主窗口中显示新数据的**“摘要”**视图。  
  
6.  若要比较这两次分析运行，请在性能资源管理器中选择这两个数据文件，右击所选文件，然后单击**“比较性能报告”**。  “比较报告”窗口随即出现在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 主窗口中。  **“增量”**列显示函数的性能值发生的更改，从早期的**“基准”**值更改为后来的**“比较”**值。  您可以从**“列”**下拉列表中选择要比较的值。  选择**“非独占样本数百分比”**。  
  
     请注意，GetPeople 和 GetNames 方法显示性能得以大大提高。  
  
## 使用检测方法分析  
 检测是一种分析方法，探查器通过这种方法将探测函数插入分析的二进制文件的特殊生成版本。  探测用于收集检测模块中函数入口和出口处以及这些函数中所有调用站点的计时信息。  检测过程对于调查与输入\/输出操作（例如写入磁盘和通过网络进行通信）有关的问题非常有用。  与采样相比，检测提供更详细的信息，但它在进程执行过程中侵入性更强，所需的开销也更大。  检测的二进制文件也比调试或发布的二进制文件大，它们不能用于部署。  
  
 在本节的演练中，我们将使用检测方法来发现更多可以在之前分析的 PeopleTrax 应用程序中优化的代码。  通过使用“摘要”视图时间线的筛选器，我们将分析重点放在将人员列表写入记事本文件的已分析应用程序中的导出数据方案上。  
  
#### 通过使用检测方法分析现有应用程序  
  
1.  如有必要，在 Visual Studio 中打开 PeopleTrax 应用程序。  
  
     确保以管理员身份运行，并确保解决方案的生成配置设置为**“发布”**。  
  
2.  在“性能资源管理器”中，单击**“检测”**。  
  
3.  在性能资源管理器工具栏上，单击**“启动并启用分析功能”**。  
  
     探查器即生成项目并开始分析应用程序。  将出现“PeopleTrax”应用程序窗口。  
  
4.  单击**“获取 People”**。  
  
     PeopleTrax 数据网格将出现数据。  
  
5.  等待大约 10 秒然后单击**“导出数据”**。  
  
     **“记事本”**将启动并显示一个包含来自 PeopleTrax 的人的列表的新文件。  等待期间，您可以更轻松地识别数据导出过程以便进行筛选。  
  
6.  关闭**“记事本”**，然后关闭**“PeopleTrax”**应用程序。  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 将生成一个性能会话报告 \(\*.vsp\)。  
  
#### 分析检测分析结果  
  
1.  报告的**“摘要”**视图中的时间线图显示程序在分析运行期间的 CPU 使用率。  导出数据操作应位于图形右侧的较大峰值或较高处。  可以筛选性能会话以只显示和分析在导出操作中收集的数据。  单击图形中导出数据操作起始点的左侧。  再单击操作的右侧。  然后单击时间线右侧链接列表中的**“按选定内容筛选”**。  
  
     **“热路径”**树显示 PeopleTrax.Form1.ExportData 方法调用的 <xref:System.String.Concat%2A> 方法消耗了大部分时间。  由于**“System.String.Concat”**也在**“大部分时间单独工作的函数”**列表顶端，因此减少该函数所消耗的时间可能是一种优化方式。  
  
2.  在任一摘要表中双击**“System.String.Concat”**，以在“函数详细信息”视图中查看更多信息。  
  
3.  可以看到 PeopleTrax.Form1.ExportData 是调用 Concat 的唯一方法。  在**“调用函数”**列表中单击**“PeopleTrax.Form1.ExportData”**，以选择作为“函数详细信息”视图目标的方法。  
  
4.  检查“函数代码视图”窗口中的方法。  请注意，没有对**“System.String.Concat”**的 literal 调用。  然而，有几处使用了 \+\= 操作数，编译器将该操作数替换为对**“System.String.Concat”**的调用。  对 .NET Framework 中的字符串的任何修改都将导致分配一个新的字符串。  .NET Framework 包括一个 <xref:System.Text.StringBuilder> 类，它针对字符串串联进行了优化。  
  
5.  若要用优化的代码替换此问题区域，请将 OPTIMIZED\_EXPORTDATA 作为条件编译符号添加到 PeopleTrax 项目中。  
  
6.  在解决方案资源管理器中，右击 PeopleTrax 项目，然后单击**“属性”**。  
  
     将出现 PeopleTrax 项目属性窗体。  
  
7.  单击**“生成”**选项卡。  
  
8.  在**“条件编译符号”**文本框中，键入 OPTIMIZED\_EXPORTDATA。  
  
9. 当出现提示时，请关闭项目属性窗体并选择**“全部保存”**。  
  
 当您再次运行应用程序时，您将看到明显的性能改进。  建议您再次运行分析会话，即使有用户可见的性能改进。  修复问题以后查看一下数据很重要，因为第一个问题可能掩盖了某些其他问题。  
  
## 请参阅  
 [概述](../profiling/overviews-performance-tools.md)   
 [入门](../profiling/getting-started-with-performance-tools.md)   
 [\/Z7、\/Zi、\/ZI（调试信息格式）](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)