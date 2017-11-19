---
title: "GetTaskSchedulersForDebugger 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 474d809f36d21b254dbb8bf302cd21bc83db88a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
检索的所有数组<xref:System.Threading.Tasks.TaskScheduler>当前处于活动状态的对象。  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **程序集：** mscorlib （mscorlib.dll) 中  
  
 由于无法访问此内部成员在.NET Framework 中，以下语法提供共同点中间语言 (CIL)。  
  
## <a name="syntax"></a>语法  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>返回值  
 数组的所有<xref:System.Threading.Tasks.TaskScheduler>中当前处于活动状态的对象<xref:System.AppDomain>。  
  
## <a name="remarks"></a>备注  
 此方法不是线程安全，不应与其他实例的同时使用<xref:System.Threading.Tasks.TaskScheduler>。 它应从调用调试器仅在调试器已挂起所有其他线程时。  
  
## <a name="see-also"></a>另请参阅  
 [Taskscheduler 计划的类](../../extensibility/debugger/taskscheduler-class-internal-members.md)