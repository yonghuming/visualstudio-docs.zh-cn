---
title: "如何： 调试 ASP.NET 异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba38521b8d3d224d6544d95b947d5f0e29727c0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-aspnet-exceptions"></a>如何：调试 ASP.NET 异常
调试异常是开发可靠的重要组成部分[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]应用程序。 有关如何调试异常的常规信息位于[管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 若要调试的未经处理的[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]例外情况之外，你必须确保调试器停止为它们。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 运行时有一个顶级异常处理程序。 因此，默认情况下，调试器绝不会在未经处理的异常中中断。 若要在引发异常时中断调试器，必须选择**发生异常时中断： 引发**设置为在该特定异常**异常**对话框。  
  
 如果已启用仅我的代码，**发生异常时中断： 引发**不会导致调试器立即中断，如果.NET Framework 方法或其他系统代码中引发异常。 执行将继续，直至调试器命中非系统代码时才中断。 因此，不必在发生异常时逐句通过系统代码。  
  
 仅我的代码向你提供了可以变得更为有用的另一个选项：**发生异常时中断： 用户未处理**。 如果为异常选择此设置，则调试器将在用户代码中中断执行，但是仅当异常没有被用户代码捕获和处理时，它才这样做。 此设置会使顶级 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 异常处理程序不起作用，因为该处理程序位于非用户代码中。  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>启用 ASP.NET 异常调试和“仅我的代码”  
  
1.  上**调试**菜单上，单击**异常**。  
  
     **异常**对话框随即出现。  
  
2.  上**公共语言运行时异常**行中，选中**引发**或**用户未处理**。  
  
     若要使用**用户未处理**设置，**仅我的代码**必须启用...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>采用 ASP.NET 异常处理的最佳做法  
  
-   在可能引发您知道如何处理的可预见异常的代码周围放置 `try ... catch` 块。 例如，如果应用程序调用 XML Web 服务或直接 SQL Server，应该将该代码在**try … catch**块中，因为有可能发生的大量异常。

## <a name="see-also"></a>另请参阅
[调试 ASP.NET 应用程序](../debugger/how-to-enable-debugging-for-aspnet-applications.md)