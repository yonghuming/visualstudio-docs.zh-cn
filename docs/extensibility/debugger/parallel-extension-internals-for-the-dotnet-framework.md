---
title: "适用于.NET Framework 并行扩展内幕 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 11
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c679d573bde8352906471b4eded7ccb9051f5959
ms.lasthandoff: 02/22/2017

---
# <a name="parallel-extension-internals-for-the-net-framework"></a>适用于.NET Framework 并行扩展内幕
本部分介绍内部类型、 方法和字段的类，可帮助您实现一个自定义的.NET Framework 并行扩展调试器。  
  
## <a name="in-this-section"></a>本节内容  
 [Task 类](../../extensibility/debugger/task-class-internal-members.md)  
 描述<xref:System.Threading.Tasks.Task?displayProperty=fullName>类</xref:System.Threading.Tasks.Task?displayProperty=fullName>的内部数据成员  
  
 [TaskScheduler 类](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 描述<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>类</xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>的内部数据成员  
  
 [ContingentProperties 类](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 内部数据成员进行了说明`System.Threading.Tasks.ContingentProperties`类。  
  
 [AsyncTaskMethodBuilder 结构](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>结构。</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>  
  
 [AsyncTaskMethodBuilder\<TResult&1;> 结构](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>结构。</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>  
  
 [AsyncVoidMethodBuilder 结构](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 内部成员进行了说明<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>结构。</xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName></xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio 调试器可扩展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [并行编程](http://msdn.microsoft.com/Library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
