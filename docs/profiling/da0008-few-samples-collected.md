---
title: "DA0008：收集的样本过少 | Microsoft Docs"
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
  - "vs.performance.rules.DATooFewSamples"
  - "vs.performance.8"
  - "vs.performance.DA0008"
  - "vs.performance.rules.DA0008"
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0008：收集的样本过少
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|规则 ID|DA0008|  
|类别|分析工具使用|  
|分析方法|采样|  
|消息|仅收集了少量样本。  请考虑延长运行时间或加快采样速度，以获取更多重要结果。|  
|规则类型|信息|  
  
## 原因  
 分析运行期间仅收集了少量样本。  
  
## 规则说明  
 使用采样方法时，应当收集在统计学角度看来足够多的样本数，才能确保结果能代表真实的程序行为。  若要最大限度地减少采样错误，您应尝试至少收集 1000 个程序指令执行行为样本。  如果不收集足够的示例，则在对分析数据进行分析时可能会被误导。  
  
## 如何解决冲突  
 请考虑延长对应用程序的分析时间，或使用更高的采样率获取有效的统计结果。  有关如何更改Visual Studio IDE的采样率，请查看 [如何：选择采样事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md) 。  有关在您使用分析工具的命令行时如何更改采样率的更多信息，请参见 [VSPerfCmd](../profiling/vsperfcmd.md) 引用中的[Timer](../profiling/timer.md)。