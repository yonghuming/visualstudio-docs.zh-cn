---
title: "如何：在分析工具报告视图中配置降噪 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.noisereduction.dialog"
helpviewer_keywords: 
  - "分析工具, 修整"
  - "分析工具, 报告降噪"
  - "分析工具, 折叠"
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 如何：在分析工具报告视图中配置降噪
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以通过限制“调用关系树”视图和“分配”视图中显示的数据量来配置性能报告以降噪。  使用降噪后，性能问题就变得较为突出。  在您分析性能报告时，这会很有帮助。  
  
 降噪配置选项包括以下设置：  
  
-   **修整** 分析报告时，该视图将删除位于该值和您配置的阈值设置内的函数（这会在以下的修整过程中说明）。  默认情况下启用修整。  
  
-   **折叠** 如果您启用折叠，将合并满足您配置的设置的路径上的连续函数（这会在以下的折叠过程中说明）。  默认情况下启用折叠。  
  
### 配置性能报告的修整  
  
1.  当“调用关系树”视图或“分配”视图显示在生成的报告中时，在**“开发人员”**菜单上，单击**“探查器”**，然后单击**“降噪选项”**。  
  
     将显示**“降噪”**对话框。  
  
2.  您可按照以下步骤启用修整：  
  
    1.  选择**“启用修整”**。  此设置为默认设置。  
  
        > [!NOTE]
        >  如果启用降噪，会在报告中显示一个信息栏。  有关更多信息，请参见[“调用关系树”视图](../profiling/call-tree-view.md)和[“分配”视图](../profiling/dotnet-memory-allocations-view.md)。  
  
    2.  通过使用**“值”**下拉列表并选择适用设置来配置值设置。  
  
    3.  通过在**“阈值”**文本框中键入百分比值来配置所需的阈值设置。  
  
    4.  若要在生成的报告中启用降噪警告，请选择**“启用降噪时显示警告”**。  此设置为默认设置。  
  
3.  若要禁用修整，请清除**“启用修整”**。  
  
4.  单击**“确定”**。  
  
### 配置性能报告的折叠  
  
1.  在**“开发人员”**菜单中，单击**“探查器”**，然后单击**“降噪选项”**。  
  
     将显示**“降噪”**对话框。  
  
2.  您可按照以下步骤启用折叠：  
  
    1.  选择**“启用折叠”**。  此设置为默认设置。  
  
        > [!NOTE]
        >  如果启用降噪，会在报告中显示一个信息栏。  有关更多信息，请参见[“调用关系树”视图](../profiling/call-tree-view.md)和[“分配”视图](../profiling/dotnet-memory-allocations-view.md)。  
  
    2.  通过使用**“值”**下拉列表并选择适用设置来配置值设置。  
  
    3.  通过在**“阈值”**文本框中键入百分比值来配置所需的阈值设置。  
  
    4.  若要在生成的报告中启用降噪警告，请选择**“启用降噪时显示警告”**。  此设置为默认设置。  
  
3.  若要禁用折叠，请清除**“启用折叠”**。  
  
4.  单击**“确定”**。  
  
## 请参阅  
 [自定义分析工具报表视图](../profiling/customizing-performance-tools-report-views.md)   
 [如何：在检测中排除或包括短函数](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)   
 [“调用关系树”视图](../profiling/call-tree-view.md)   
 [“分配”视图](../profiling/dotnet-memory-allocations-view.md)