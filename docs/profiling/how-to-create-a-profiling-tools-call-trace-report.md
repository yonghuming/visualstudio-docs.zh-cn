---
title: "如何：创建分析工具调用跟踪报告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW [Visual Studio ALM], 查看数据"
  - "性能工具, 查看 ETW 数据"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 如何：创建分析工具调用跟踪报告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的调用跟踪报告列出您的应用程序函数每个入口点和出口点的计时信息，以及您的函数对其他函数的每次调用的计时信息。  仅当使用检测方法收集时，调用跟踪报告才可用于分析数据。  
  
> [!NOTE]
>  不能在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中显示调用跟踪报告。  必须使用 **VSPerfReport** 命令行工具才能生成逗号分隔值 \(.csv\) 或 XML 文件。  有关此工具的更多信息，请参见 [VSPerfReport](../profiling/vsperfreport.md)。  
  
### 创建调用跟踪报告  
  
1.  打开**“命令提示”**窗口。  
  
2.  在命令提示符处，键入下列命令：  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|分析工具命令行工具的路径。  有关详细信息，请参阅 [指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。|  
    |*VSPFile*|分析数据（.vsp 或 .vsps）文件。  接受完整路径和部分路径。|  
    |Xml|生成 XML 格式的报告。|  
  
## 请参阅  
 [如何：收集 Windows 事件跟踪 \(ETW\) 数据](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [分析工具 API](../profiling/profiling-tools-apis.md)