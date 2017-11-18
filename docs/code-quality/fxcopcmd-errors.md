---
title: "FxCopCmd 错误 |Microsoft 文档"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.openlocfilehash: 2439b04c921de6e06b98bd1bb5a9fc0af3ea56d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="fxcopcmd-errors"></a>FxCopCmd 错误
FxCopCmd 不考虑所有错误都以是致命的。 如果 FxCopCmd 具有足够的信息来执行部分分析，它将执行的分析和报告的错误的发生。 错误代码，它是一个 32 位整数，包含对应于错误的数字值的按位组合。  
  
 下表介绍 FxCopCmd 返回的错误代码：  
  
|错误|数字值|  
|-----------|-------------------|  
|没有错误|0x0|  
|分析错误|0x1|  
|规则例外|0x2|  
|项目加载错误|0x4|  
|程序集加载错误|0x8|  
|规则库加载错误|0x10|  
|导入报表加载错误|0x20|  
|输出错误|0x40|  
|命令行开关错误|0x80|  
|初始化错误|0x100|  
|程序集引用错误|0x200|  
|BuildBreakingMessage|0x400|  
|未知的错误|0x1000000|  
  
 分析错误则返回的错误。 它指示无法完成分析。 如果适用，错误代码还包含错误的根本原因。 以下情况下将生成错误：  
  
-   分析无法执行由输入不足所导致。  
  
-   分析引发了 FxCopCmd 未处理的异常。  
  
-   指定的项目文件未找到或者已损坏。  
  
-   未指定输出选项，或无法写入文件。  
  
    > [!NOTE]
    >  FxCopCmd 返回代码"程序集引用错误"0x200 本身是一个警告，而不是错误。 此返回代码指示已找到缺少的间接引用，但 FxCopCmd 却能够处理它们。 它是一条警告，存在一些分析结果可能已泄露的可能性。 "程序集引用错误"返回代码视为错误，当它与任何其他返回代码相结合。  
  
## <a name="see-also"></a>另请参阅  
 [代码分析应用程序错误](../code-quality/code-analysis-application-errors.md)