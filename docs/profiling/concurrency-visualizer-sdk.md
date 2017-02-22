---
title: "并发可视化工具 SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 并发可视化工具 SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过使用并发可视化工具 SDK 查看并发可视化工具中的其他信息，您可以检测源代码。  可以将附加代码中的数据与您代码中的阶段和事件关联。  这些额外的可视化为 *标记*。有关介绍性演练，请参见 [介绍并发可视化工具 SDK](http://go.microsoft.com/fwlink/?LinkId=235405)。  
  
## 属性  
 标志、跨度和消息都有两个属性：类别和重要性。  在 [高级设置](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 对话框，您可以使用这些属性筛选显示的标记集。  此外，这两个属性影响标记的可视化表示形式。  例如，标志的大小用于表示重要性。  此外，颜色用于指示类别。  
  
## 基本用法  
 并发可视化工具公开可以用于生成标记的默认提供程序。  提供程序与并发可视化工具已一起注册，因此您无需执行任何其他操作便可以使标记显示在 UI 中。  
  
### C\# 和 Visual Basic  
 在 C\# 和其他托管代码中，通过调用 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>使用默认提供程序。  它为生成标记暴漏四个函数：<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>、<xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A>和 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>。  有这些函数的多个重载，取决于您是否希望对属性使用默认值。最简单的重载采用字符串参数该字符串描述特定事件。  描述在并发可视化工具报告中显示。  
  
##### 添加 SDK 支持到 C\# 或 Visual Basic 项目  
  
1.  在菜单栏上，依次选择 **分析**，**并发可视化工具**，**将 SDK 添加到项目中**。  
  
2.  选择要访问 SDK 的项目，然后选择 **将 SDK 添加到所选项目中** 按钮。  
  
3.  添加 imports 或 using 到您的代码。  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 在 C\+\+，创建 [marker\_series 类](../profiling/marker-series-class.md) 对象并使用它来调用函数。`marker_series` 类暴露三个函数来生成标记， [marker\_series::write\_flag 方法](../profiling/marker-series-write-flag-method.md)，[marker\_series::write\_message 方法](../profiling/marker-series-write-message-method.md)，和 [marker\_series::write\_alert 方法](../profiling/marker-series-write-alert-method.md)。  
  
##### 添加 SDK 支持到 C\+\+ 或 C\# 项目  
  
1.  在菜单栏上，依次选择 **分析**，**并发可视化工具**，**将 SDK 添加到项目中**。  
  
2.  选择要访问 SDK 的项目，然后选择 **将 SDK 添加到所选项目中** 按钮。  
  
3.  对于 C\+\+，include `cvmarkersobj.h`。  对于 C，include `cvmarkers.h`。  
  
4.  添加 using 语句到代码。  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  创建`marker_series` 对象，并将传递给 `span` 对象。  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## 自定义用法  
 对于高级方案，并发可视化 SDK 工具公开更多控件。两个主要概念关联于更高级的方案：标记提供程序和标记系列。  标记提供程序为不同的 ETW 提供程序 \(每个都具有不同的 GUID\)。  标记系列是由一个提供程序生成的串行事件通道。  可以使用它们组织由标记提供程序生成的事件。  
  
#### 在 C\# 或 Visual Basic 项目中使用新的标记提供程序。  
  
1.  创建 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> 对象。带 GUID 的构造函数。  
  
2.  若要注册提供程序，打开并发可视化工具 [高级设置](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 对话框。选择 **标记** 选项卡然后选择 **添加新提供程序** 按钮。  在 [高级设置](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 对话框中输入用于创建提供程序和提供程序描述的 GUID。  
  
#### 在 C\+\+ 或 C 项目中使用新的标记提供程序。  
  
1.  使用 `CvInitProvider` 函数初始化一个 PCV\_PROVIDER。构造函数带有一个 GUID\* 和 PCV\_PROVIDER\*。  
  
2.  若要注册提供程序，请打开 [高级设置](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 对话框。选择 **标记** 选项卡然后选择 **添加新提供程序** 按钮。  在此对话框中，输入用于创建提供程序和提供程序描述的 GUID。  
  
#### 在 C\# 或 Visual Basic 项目中使用标记系列。  
  
1.  通过使用 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> 对象创建新的 <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>对象，然后用它再直接生标记事件。  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### 在 C\+\+ 项目中使用标记系列  
  
1.  创建 `marker_series` 对象。您可以从此新系列生成事件。  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### 在 C 项目中使用标记系列  
  
1.  使用 `CvCreateMarkerSeries` 函数创建 PCV\_MARKERSERIES。  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[C\+\+ 库参考](../profiling/cpp-library-reference.md)|为 C\+\+ 描述并发可视化工具 API。|  
|[C 库参考](../profiling/c-library-reference.md)|为 C 描述并发可视化工具 API。|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|为托管代码描述并发可视化工具 API。|  
|[并发可视化工具](../profiling/concurrency-visualizer.md)|针对使用并发方法生成的且包括线程执行数据的分析数据文件，提供有关视图和报告的参考信息。|