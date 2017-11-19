---
title: "调试器组件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec2b7a18dac9616db1743a50539c2860caca2e26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-components"></a>调试器组件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试器作为 VSPackage 实现和管理整个调试会话。 调试会话过程包括以下元素：  
  
-   **调试包：** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试器提供了相同的用户界面，不论正在调试。  
  
-   **会话调试管理器 (SDM):**提供一致的编程接口，到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试器对各种的调试引擎的管理。 由实现[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   **过程调试管理器 (PDM):**管理，所有运行的实例为[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以是或正在调试的所有程序的列表。 由实现[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   **调试引擎 (DE):**负责监视正在调试的程序进行通信的 SDM 和 PDM，正在运行的程序的状态并提供对进行实时分析的表达式计算器和符号提供程序与之交互程序的内存和变量的状态。 由实现[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（为它支持的语言） 和第三方供应商想要支持其自己的运行的时。  
  
-   **表达式计算器 (EE):**用于动态评估变量和表达式的用户提供的程序已停止的特定点时提供支持。 由实现[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（为它支持的语言） 和第三方供应商想要支持他们自己的语言。  
  
-   **符号提供程序 (SP):**也称为符号处理程序，映射程序的调试符号到该程序的运行实例，以便可以提供有意义的信息 （如代码源级调试和表达式计算）。 由实现[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（为公共语言运行时 [CLR] 符号和程序数据库 [PDB] 符号文件格式） 和由第三方供应商有其自己的存储调试信息的专有方法。  
  
 下图显示在 Visual Studio 调试器这些元素之间的关系。  
  
 ![调试组件概述](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>本节内容  
 [调试包](../../extensibility/debugger/debug-package.md)  
 讨论了在中运行的调试包[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell 和处理所有 UI。  
  
 [进程调试管理器](../../extensibility/debugger/process-debug-manager.md)  
 概述 PDM，即，可以调试该进程的管理器的功能。  
  
 [会话调试管理器](../../extensibility/debugger/session-debug-manager.md)  
 定义 SDM，向 IDE 提供调试会话的统一的视图。 SDM 管理 DE。  
  
 [调试引擎](../../extensibility/debugger/debug-engine.md)  
 记录 DE 提供调试服务。  
  
 [操作模式](../../extensibility/debugger/operational-modes.md)  
 提供三种模式可以 IDE 的概述： 设计模式、 运行模式下和中断模式。 此外讨论了转换机制。  
  
 [表达式计算器](../../extensibility/debugger/expression-evaluator.md)  
 在运行时说明 EE 的用途。  
  
 [符号提供程序](../../extensibility/debugger/symbol-provider.md)  
 讨论如何，在实现中，符号提供程序的计算结果的变量和表达式。  
  
 [类型可视化工具和自定义查看器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 讨论什么类型可视化工具和自定义查看器是，哪些角色中同时支持它起的表达式计算器。  
  
## <a name="related-sections"></a>相关章节  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 说明 DE 如何同时运行代码、 文档和表达式评估上下文中。 描述，为每个三个上下文、 位置、 位置或评估与它相关。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向不同的调试任务，如启动程序和计算表达式。  
  
## <a name="see-also"></a>另请参阅  
 [入门](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)