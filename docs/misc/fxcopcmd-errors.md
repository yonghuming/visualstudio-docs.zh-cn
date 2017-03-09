---
title: "FxCopCmd 错误 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FxCopCmd 错误"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# FxCopCmd 错误
FxCopCmd 不会将所有错误都视为严重错误。  如果 FxCopCmd 具有足够的信息执行部分分析，它将执行该分析并报告发生的错误。  错误代码（32 位整数）包含与错误对应的数值的按位组合。  
  
 下表介绍了 FxCopCmd 返回的错误代码：  
  
|错误|数值|  
|--------|--------|  
|无错误|0x0|  
|分析错误|0x1|  
|规则异常|0x2|  
|项目加载错误|0x4|  
|程序集加载错误|0x8|  
|规则库加载错误|0x10|  
|导入报告加载错误|0x20|  
|输出错误|0x40|  
|命令行开关错误|0x80|  
|初始化错误|0x100|  
|程序集引用错误|0x200|  
|BuildBreakingMessage|0x400|  
|未知错误|0x1000000|  
  
 为严重错误返回分析错误。  它指明分析未能完成。  适用情况下，错误代码还包含严重错误的根本原因。  下列情况下将生成严重错误：  
  
-   由于输入不足导致分析未能执行。  
  
-   分析引发的异常不是由 FxCopCmd 处理。  
  
-   未能找到指定的项目文件，或文件已损坏。  
  
-   未指定输出选项或未能写入文件。  
  
    > [!NOTE]
    >  FxCopCmd 返回代码“程序集引用错误”0x200 本身是一个警告，而非一个错误。  此返回代码表明，发现缺少间接引用，但此 FxCopCmd 能够处理它们。  它是一个警告，指出有些分析结果可能已受到影响。  当“程序集引用错误”返回代码与任何其他返回代码一同出现时，请将其视为一个错误。  
  
## 请参阅  
 [代码分析应用程序错误](../code-quality/code-analysis-application-errors.md)