---
title: ".NET framework 的并行扩展内部 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ed417d9f63a90d539d104fb209b58703d10ccef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET framework 的并行扩展内部机制
本部分介绍了内部类型、 方法和字段的类，用于帮助你实现一个自定义的.NET framework 的并行扩展的调试器。  
  
## <a name="in-this-section"></a>本节内容  
 [任务类](../../extensibility/debugger/task-class-internal-members.md)  
 内部数据成员进行了说明<xref:System.Threading.Tasks.Task?displayProperty=fullName>类。  
  
 [Taskscheduler 计划的类](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 内部数据成员进行了说明<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>类。  
  
 [ContingentProperties 类](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 内部数据成员进行了说明`System.Threading.Tasks.ContingentProperties`类。  
  
 [AsyncTaskMethodBuilder 结构](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>结构。  
  
 [AsyncTaskMethodBuilder\<TResult > 结构](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>结构。  
  
 [AsyncVoidMethodBuilder 结构](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>结构。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio 调试器扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [并行编程](/dotnet/standard/parallel-programming/index)