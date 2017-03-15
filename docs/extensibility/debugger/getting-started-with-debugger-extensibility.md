---
title: "调试器可扩展性入门 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
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
ms.openlocfilehash: 258fcfcc97d0a6b1455ec60201527cde3e87f9b8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-debugger-extensibility"></a>调试器可扩展性入门
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供所必须具有创建和自定义调试器使用的组件来调试程序中的信息[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]环境。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试已添加派生自上以前执行的测试的广泛可用性改进[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试器。 您可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]多语言应用程序中，或你单步调试可以实现在调试应用程序和多语言解决方案时，动态上编辑的变量。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试是执行的进程外与正在调试的程序，因此该应用程序的进程空间中较少受侵入。 因此，很方便地使用调试器编写交互的组件，而不会影响调试程序。  
  
 最大程度利用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，您应该熟悉以下︰  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成的开发环境 (IDE)  
  
-   C + + 编程语言  
  
-   ATL COM  
  
## <a name="in-this-section"></a>本节内容  
 [扩展调试器的路线图](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 概括介绍了实现在您的产品，具体取决于您的编译器和相应的输出中进行调试的过程。  
  
 [调试程序组件](../../extensibility/debugger/debugger-components.md)  
 概述[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试组件，其中包括调试引擎 (DE)、 表达式计算器 (EE) 和符号处理程序 (SH)。  
  
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)  
 描述调试的主要体系结构概念。  
  
 [调试器上下文](../../extensibility/debugger/debugger-contexts.md)  
 介绍了调试引擎 (DE) 的运行方式同时代码、 文档和表达式计算上下文中。 描述，每个算法的三个上下文、 位置、 位置或评估与它相关。  
  
 [调试任务](../../extensibility/debugger/debugging-tasks.md)  
 包含指向各种调试任务，如启动程序，然后计算表达式。
