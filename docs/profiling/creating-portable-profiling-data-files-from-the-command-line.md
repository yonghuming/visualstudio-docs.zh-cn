---
title: "从命令行创建可移植的分析数据文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 从命令行创建可移植的分析数据文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要更容易地共享分析数据，可以使用 [VSPerfReport](../profiling/vsperfreport.md)，命令行工具将分析运行的符号嵌入到 .vsp 文件中。  
  
 还可以创建经过预先分析的分析数据 \(.vsps\) 文件，此文件较小，在 IDE 中可以更迅速地加载。  
  
> [!NOTE]
>  请确保对 **VSPerfReport** 可提供符号 \(.pdb\) 文件。  有关详细信息，请参阅[如何：从命令行指定符号文件位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)。  
>   
>  有关 **VSReport** 路径的信息，请参见[指定命令行工具的路径](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  无法筛选 .vsps 文件中的分析数据。  
  
### 将分析运行的符号嵌入到分析数据 \(.vsp\) 文件中  
  
-   在命令提示符窗口中，键入以下命令：  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/PackSymbols**  
  
     默认情况下，以 .vsp 文件的基名称命名 .vsps 文件。  可以使用 **Output** 选项指定备用名称。  
  
### 创建摘要分析数据文件  
  
-   在命令提示符窗口中，键入以下命令：  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/SummaryFile** \[**\/Output:**\<File Name\>\]  
  
     默认情况下，以 .vsp 文件的基名称命名 .vsps 文件。  可以使用 **Output** 选项指定备用名称。