---
title: "Task 类的内部成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5937d37cfed89ee7f10779f764b8d78d370eb362
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="task-class---internal-members"></a>任务类的内部成员
本主题介绍的内部成员<xref:System.Threading.Tasks.Task?displayProperty=fullName>帮助你的类实现自定义调试器。 有关此类的常规信息，请参阅<xref:System.Threading.Tasks.Task>参考主题。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集：** mscorlib （mscorlib.dll) 中  
  
 由于无法访问这些内部成员在.NET Framework 中，以下语法提供共同点中间语言 (CIL)。  
  
## <a name="syntax"></a>语法  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|名称|描述|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion 方法](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|设置或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 状态位。|  
|[NotifyDebuggerOfWaitCompletion 方法](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|占位符方法用作由调试器的断点目标。|  
  
### <a name="fields"></a>字段  
  
|名称|描述|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|表示要在中执行的代码的委托<xref:System.Threading.Tasks.Task>对象。|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|将存储的其他属性<xref:System.Threading.Tasks.Task>对象。|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|为支持字段<xref:System.Threading.Tasks.Task?displayProperty=fullName>父属性。|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|存储的当前状态有关的信息<xref:System.Threading.Tasks.Task>对象。|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|一个表示由该操作将使用的数据的对象。|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|为支持字段<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>属性。|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|下一步可用标识符<xref:System.Threading.Tasks.Task>对象。|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|指示任务已取消之前它已达到运行状态，或任务已对其取消和完成没有出现异常。|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|指示任务正在运行。|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|指示由于未经处理的异常完成的任务。|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|指示任务已成功完成执行。|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|指示任务已完成执行其委托，正在隐式等待附加的子任务完成。|  
  
## <a name="remarks"></a>备注  
 下面的内部方法是对调试器引擎有用，因为它们标记为入口<xref:System.Threading.Tasks.Task>执行代码：  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework 的并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)