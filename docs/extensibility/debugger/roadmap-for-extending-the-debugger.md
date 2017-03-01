---
title: "用于扩展调试器路线图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 49df627aa42cd6cc6ac1430e4e68694fa51a2fc1
ms.lasthandoff: 02/22/2017

---
# <a name="roadmap-for-extending-the-debugger"></a>扩展调试器的路线图
本文档提供了指南和参考信息扩展[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]调试器与[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试文档包含示例、 全面的参考和演示自定义调试器的典型方法的几个典型方案。  
  
 您的编译器和其输出确定您需要实现调试您的产品中执行的操作。 如果您的编译器︰  
  
-   面向 Windows 本机操作系统并将写入。PDB 文件，您可以使用本机代码调试引擎 (DE)，它集成到调试程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 不需要实现 DE 或表达式计算器。 表达式计算器是面向 c + + 编程语言的语法。  
  
-   生成的 Microsoft 中间语言 (MSIL) 输出时，可以使用由托管的代码的调试引擎 DE，它还集成到调试程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 因此，您只需实现的表达式计算器。 示例表达式计算器会为您提供。 有关详细信息，请参阅下列主题：  
  
     [表达式计算](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [计算表达式](../../extensibility/debugger/evaluating-expressions.md)  
  
     [表达式计算上下文](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [在中断模式下的表达式计算](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [编写公共语言运行时表达式计算器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   专有操作系统或其他某个运行时环境的目标，您需要编写您自己 DE。 提供创建简单 DE 使用 ATL COM 的教程。 有关详细信息，请参阅下列主题：  
  
     [创建自定义调试引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [教程︰ 构建使用 ATL COM 的调试引擎](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [实现端口提供程序](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [示例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>另请参阅  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
