---
title: "如何：重新指定检测后的二进制文件的位置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "二进制文件, 已检测"
  - "检测, 检测的二进制文件"
  - "检测的二进制文件和重新指定"
  - "分析工具, 检测的二进制文件"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：重新指定检测后的二进制文件的位置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在检测期间，探测器将插入二进制文件来评估应用程序性能。 通过选择重定位已检测的二进制文件，将检测原始二进制文件的副本，并将其放在指定位置。 如果不想要探查器重命名原始的二进制文件，可以选择此选项。 如果没有重定位该二进制文件，则将覆盖该二进制文件的原始版本。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### 若要重定位已检测的二进制文件  
  
1.  在“性能资源管理器”中，右键单击性能会话，然后单击“属性”。  
  
2.  在“属性页”中，单击“二进制”属性。  
  
3.  选择“重定位已检测的二进制文件”复选框。  
  
4.  为已检测的二进制文件指定位置。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)