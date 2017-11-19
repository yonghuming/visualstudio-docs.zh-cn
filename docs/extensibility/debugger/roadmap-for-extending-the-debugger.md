---
title: "用于扩展调试器路线图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af86f2b8daeffeb700b619c4ba0d9cbb00700dd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="roadmap-for-extending-the-debugger"></a>用于扩展调试器路线图
本文档提供指南和参考信息，用于扩展[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]调试器与[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试文档包括示例、 全面的参考和演示自定义调试器的典型方法的几种代表性方案。  
  
 你的编译器和其输出确定需要要做，以实现在您的产品中进行调试。 如果你的编译器：  
  
-   面向 Windows 本机操作系统并将写入。PDB 文件，你可以调试程序的集成到的本机代码调试引擎 (DE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 不需要实现 DE 或表达式计算器。 为 c + + 编程语言的语法编写，表达式计算器。  
  
-   生成的 Microsoft 中间语言 (MSIL) 输出，可以使用托管的代码调试引擎 DE，这也集成到调试程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，你只需实施的表达式计算器。 为你提供了示例表达式计算器。 有关详细信息，请参阅下列主题：  
  
     [表达式计算](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [计算表达式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [表达式计算上下文](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [中断模式中的表达式计算](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [编写公共语言运行时表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   操作系统或某些其他运行时环境的专有的目标，你需要编写你自己 DE。 提供创建简单 DE 使用 ATL COM 的教程。 有关详细信息，请参阅下列主题：  
  
     [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [教程： 构建使用 ATL COM 调试引擎](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [实现端口提供程序](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [示例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>另请参阅  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)