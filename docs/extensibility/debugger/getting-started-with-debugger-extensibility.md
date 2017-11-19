---
title: "Getting Started with 调试器扩展性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1419f4e45aefed59aa36b249568a53a47ad3c459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Getting Started with 调试器扩展性
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供必须具有创建和自定义使用调试程序中的调试器组件的信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试具有添加派生自上以前测试执行的大量可用性的改进[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试器。 你可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试单步执行的多语言应用程序中，也可以实现即时上调试应用程序和多语言解决方案时编辑的变量。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试执行的进程外与正在调试的程序，因此在应用程序的进程空间少受侵入。 因此，并更轻松地写入与调试器的交互的组件，而不会影响调试程序。  
  
 最大效用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，你应该熟悉以下：  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)  
  
-   C + + 编程语言  
  
-   ATL COM  
  
## <a name="in-this-section"></a>本节内容  
 [扩展调试器的路线图](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 概述了实现在产品中，具体取决于你的编译器和其输出调试的过程。  
  
 [调试器组件](../../extensibility/debugger/debugger-components.md)  
 提供的概述[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试组件，包括调试引擎 (DE)、 表达式计算器 (EE) 和符号处理程序 (SH)。  
  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 说明调试引擎 (DE) 如何同时运行代码、 文档和表达式评估上下文中。 描述，为每个三个上下文、 位置、 位置或评估与它相关。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向不同的调试任务，如启动程序和计算表达式。