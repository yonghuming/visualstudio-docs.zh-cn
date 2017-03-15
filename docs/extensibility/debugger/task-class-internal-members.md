---
title: "Task 类的内部成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
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
ms.openlocfilehash: 21acb0a52dfde7ad565e9764e2a333a9925a2171
ms.lasthandoff: 02/22/2017

---
# <a name="task-class---internal-members"></a>Task 类的内部成员
本主题介绍的内部成员的<xref:System.Threading.Tasks.Task?displayProperty=fullName>类来帮助您实现自定义调试器。</xref:System.Threading.Tasks.Task?displayProperty=fullName> 有关此类的常规信息，请参阅<xref:System.Threading.Tasks.Task>参考主题。</xref:System.Threading.Tasks.Task>  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName></xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集︰** mscorlib （在 mscorlib.dll)  
  
 由于无法在.NET Framework 中访问这些内部成员，下面的语法提供通用中间语言 (CIL)。  
  
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
  
|名称|说明|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion 方法](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|设置或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 状态位。|  
|[NotifyDebuggerOfWaitCompletion 方法](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|调试程序所使用的断点目标的占位符方法。|  
  
### <a name="fields"></a>字段  
  
|名称|说明|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|表示要在中执行的代码的委托<xref:System.Threading.Tasks.Task>对象。</xref:System.Threading.Tasks.Task>|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|将存储的其他属性<xref:System.Threading.Tasks.Task>对象。</xref:System.Threading.Tasks.Task>|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|有关支持字段<xref:System.Threading.Tasks.Task?displayProperty=fullName>parent 属性。</xref:System.Threading.Tasks.Task?displayProperty=fullName>|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|存储的当前状态有关的信息<xref:System.Threading.Tasks.Task>对象。</xref:System.Threading.Tasks.Task>|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|表示将由该操作使用的数据的对象。|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|有关支持字段<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>属性。</xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName>|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|下一步提供标识符<xref:System.Threading.Tasks.Task>对象。</xref:System.Threading.Tasks.Task>|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|指示任务已取消之前它已经达到运行状态，或者任务确认其取消和完成无一例外。|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|指示任务正在运行。|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|指示任务已完成，由于未经处理的异常。|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|指示任务已成功完成执行。|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|指示任务已完成执行其委托，隐式等待附加的子任务完成。|  
  
## <a name="remarks"></a>备注  
 下面的内部方法非常有用到调试器引擎，因为它们标记为入口<xref:System.Threading.Tasks.Task>代码执行︰</xref:System.Threading.Tasks.Task>  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [适用于.NET Framework 并行扩展内幕](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
