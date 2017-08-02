---
title: "针对 Visual Studio 的 R 工具示例项目 | Microsoft Docs"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>针对 Visual Studio 的 R 工具示例项目

此示例集合可助你开始使用 R、针对 Visual Studio 的 R 工具 (RTVS) 以及 Microsoft R Server：

1. 下载[示例 zip 文件](https://github.com/Microsoft/RTVS-docs/archive/master.zip)并将其解压到选择的文件夹。
1. 打开 `examples/Examples.sln`，可看到项目中的两个文件夹：

    - “初探 R”为 R 新用户提供简要介绍。
    - “MRS 和机器学习”举例说明如何将 R 和 Microsoft R Server 用于机器学习。

## <a name="a-first-look-at-r"></a>初探 R

此示例通过源文件中的大量注释深入介绍 R。 体验以下两个示例的最佳方式是将光标置于文件顶部，然后按 Ctrl+Enter 向“R 交互”窗口发送每一行（一次一行），可在该窗口中查看结果。 请注意：某些行会花费一到两分钟的时间来安装包。

- `1-Getting Started with R.R` 介绍了许多 R 基础知识，包括使用包、加载和分析数据以及绘图等。

    ![1-Getting Started with R.R 示例的示例输出](~/rtvs/media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` 引入了 ggplot2 图形包，该图形包以其极具视觉吸引力的绘图和简单的语法而著称。 此示例直观的展示斐济的地震数据。

    ![2-Introduction to ggplot2.R 示例的示例输出](~/rtvs/media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server 和机器学习

此示例集合演示如何使用 R 和 Microsoft R Server 创建机器学习模型，以及如何利用 [Microsoft R Server (MRS)](http://aka.ms/rtvs-msft-r) 的功能。 请注意，需要安装 MRS 才能使用 `MRS` 在标题和标注的位置运行脚本。

与所有示例一样，进行体验的一个好方法是打开文件，将光标置于顶部，然后按 Ctrl+Enter 逐行逐过程执行代码。 另请参阅每个文件夹中的 Markdown 文件，了解其他详细信息。

- `Benchmarks` 运行大量计算密集型基准，显示使用 Microsoft R Open 和 Intel Math Kernel Library (MKL) 进行快速的并行线性代数计算可能提升的性能。 借助模拟数据，它仔细比较了分别使用两个线程和一个线程来进行特定矩阵相关计算的情况。   

    ![基准绘图示例](~/rtvs/media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` 使用 Microsoft R Server，根据历史数据集创建用于单车租赁的需求预测模型。 

- `Data_Exploration` 包含三个脚本：  
    - `Import Data from URL.R` 演示如何将 URL 标识的数据文件加载到 R 中。
    - `Import Data from URL to xdf.R` 演示如何将 URL 标识的数据文件以 xdf 文件的形式加载到 Microsoft R Server。 （需要 MRS。）
    - `Using ggplot2.R` 是`A First Look at R/2-Introduction to ggplot2.R` 示例的扩展，它更深入地介绍了 ggplot2 的功能，包括交互式 3D 绘图。

        ![使用 ggplot2.R 示例的输出](~/rtvs/media/samples-3d-interactive.png)

- `Datasets` 包含其他示例使用的三个 `.csv` 文件
- `Flight_Delays_Prediction_with_R` 和 `Flight_Delays_Prediction_with_MRS` 演示如何使用 R 机器学习、历史实时性能和天气数据预测航班延误。 
- `Machine learning`包含三个学习示例，演示如何预测航班延误、房价和单车租赁，以及如何针对实际问题应用 R 和 MRS。 它们还演示如何使用多个热门机器学习模型，以及如何使用 [Azure 机器学习](https://azure.microsoft.com/services/machine-learning/)工作区将这些模型部署为 Azure Web 服务。

- `R_MRO_MRS_Comparison` 是一个含有 6 部分的比较，展示 R、Microsoft R Open 和 Microsoft R Server 在命令、语法、构造和性能方面的异同。

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Microsoft R Open 和 Microsoft R Server 有什么特别之处？

[Microsoft R Open](http://aka.ms/rtvs-r-open) 是 Microsoft R 的分发，与 [CRAN R](https://cran.r-project.org/) 相比有两个重大差异：

1. 如果与 [Intel Math Kernel Libraries](https://software.intel.com/intel-mkl) 配合使用，可获得[更好的计算性能](https://mran.revolutionanalytics.com/rro/#intelmkl1)。 可从 Microsoft 免费获取这些内容，以便与 Microsoft R Open 配合使用。

1. [可重现 R 工具包](https://mran.revolutionanalytics.com/rro/#reproducibility)，可确保用于生成 R 程序的库始终都可供想要重现操作的其他人员使用。

[Microsoft R Server](http://aka.ms/rtvs-msft-r) 是 R 的扩展，可用于更快地处理更多数据。 它为 R 赋予了两项强大的功能：

1. 大型数据集。 MRS 可以处理各种来源（包括 Hadoop 群集、数据库和数据仓库）中的内存不足数据。 再也不会受限于 RAM。

1. 并行多核处理。 MRS 可在可用的所有计算资源中高效分发计算。 在个人工作站或远程群集上，MRS 将更快获得答案。

以下比较显示，进行某些矩阵计算时，使用 MKL 的 MRS 和 MRO 可实现的性能明显优于不使用 MKL 的 R 和 MRO。 此计算中使用模拟数据：

![比较使用 MKL 的 MRS 和 MRO 与不使用 MKL 的 R 和 MRO](~/rtvs/media/samples-speed-comparison.png)

有关 R 与 MRO 和 MRS 的技术比较，请参阅关于该主题的 [Lixun Zhang 详细讨论](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html)。

然后，下图比较生成逻辑回归模型所用的运行时间（秒），从而预测计划的乘客航班到达时间是否会延误超过 15 分钟。 行数的微小增加将会导致 CRAN R 中的运行时间显著增加，而 MRS 的增加量仅约为行数的两倍。 有关此基准的详细信息，请参阅 `Benchmarks/rxGlm_benchmark.R` 示例。

![rxGlm 基准](~/rtvs/media/samples-rxGLM-benchmark.png)

