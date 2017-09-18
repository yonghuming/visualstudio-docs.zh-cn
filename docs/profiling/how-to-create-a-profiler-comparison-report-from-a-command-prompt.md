---
title: "如何：从命令提示符下创建探查器比较报告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：从命令提示符下创建探查器比较报告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以生成 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具报告，用于比较两个分析数据（.VSP 或 .VSPS）文件的性能数据。  报告显示了从一个分析会话到另一个分析会话发生的差异、性能衰退和提高。  报告中的值表示与所指定首个文件的基准之间的增量（即变化）。  此增量是通过确定旧值（基准值）与新分析所得结果值之差计算而得。  探查器数据的比较基于代码中的函数、应用程序中的模块、行、指令指针 \(IP\) 和类型。  
  
 若要列出比较类别和字段的标识符，请键入以下命令行：  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 使用以下语法创建比较报告：  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 可以向 **VSPerfReport \/diff** 命令行添加下表中的选项。  
  
|选项|说明|  
|--------|--------|  
|**DiffThreshold:**\[*Value*\]|如果差异低于此百分比阀值，则忽略该差异。  另外，不会显示其值低于此阈值的新数据。|  
|**DiffTable:** *TableName*|使用此表比较文件。  默认情况下，使用函数表。  指定 **VSPerfReport \/querydifftables** 中列出的标识符。|  
|**DiffColumn:** *ColumnName*|使用此列对值进行比较。  默认情况下，使用独占样本百分比列。  指定 **VSPerfReport \/querydifftables** 中列出的标识符。|