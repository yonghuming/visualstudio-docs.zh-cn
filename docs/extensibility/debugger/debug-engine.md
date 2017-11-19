---
title: "调试引擎 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2db510e81231f7802d686b21a977c271a66c5d79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="debug-engine"></a>调试引擎
调试引擎 (DE) 适用于提供调试服务，例如执行控件、 断点及表达式评估的解释程序或操作系统。 DE 负责监视正在调试的程序的状态。 不要使用实现此目的，DE 任何方法将中支持的运行时，可供它，无论是由运行时提供的 CPU 中或从 Api。  
  
 例如，公共语言运行时 (CLR) 提供机制来监视正在运行的程序通过 ICorDebugXXX 接口。 支持 CLR DE 使用相应的 ICorDebugXXX 接口来跟踪正在调试的托管的代码程序。 它然后通信会话调试管理器 (SDM)，将转发到此类信息的状态的任何更改[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
> [!NOTE]
>  调试引擎面向特定的运行时，即，在其中程序正在调试运行系统。 CLR 用于托管代码的运行时，Win32 运行时用于本机 Windows 应用程序。 如果你创建的语言可以面向这些两个运行时，之一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]已提供必要的调试引擎。 你必须实现所有是表达式计算器。  
  
## <a name="debug-engine-operation"></a>调试引擎操作  
 监视服务通过 DE 接口实现，并可能导致不同的运行模式之间的转换调试包。 有关详细信息，请参阅[运行模式](../../extensibility/debugger/operational-modes.md)。 通常是每个运行时环境的只有一个 DE 实现。  
  
> [!NOTE]
>  尽管有单独的 DE 实现，对于 TRANSACT-SQL 和[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]，VBScript 和[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]共享单个 DE。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试启用调试引擎运行两种方式之一： 在与相同的进程[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell，或在与目标程序相同的进程正在调试。 当正在调试的进程是实际在解释器下, 运行的脚本和的调试引擎必须具备精通解释程序的监视脚本时，通常会出现后一种形式。 请注意，在这种情况下，该解释器是实际运行时;调试引擎是针对特定运行时实现。 此外，实现单个 DE 可以拆分跨进程和计算机边界 （例如，远程调试）。  
  
 DE 公开[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]调试接口。 所有通信都是通过 com。 是否在进程、 进程外或另一台计算机上加载 DE，它不会影响组件通信。  
  
 DE 适用于要为其启用 DE 代表该特定的运行时，若要了解表达式语法的表达式计算器组件。 DE 也适用于要访问由语言编译器生成的符号调试信息的符号处理程序组件。 有关详细信息，请参阅[表达式计算器](../../extensibility/debugger/expression-evaluator.md)和[符号提供程序](../../extensibility/debugger/symbol-provider.md)。  
  
## <a name="see-also"></a>另请参阅  
 [调试器组件](../../extensibility/debugger/debugger-components.md)   
 [表达式计算器](../../extensibility/debugger/expression-evaluator.md)   
 [符号提供程序](../../extensibility/debugger/symbol-provider.md)