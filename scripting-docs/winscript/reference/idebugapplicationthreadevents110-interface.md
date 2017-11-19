---
title: "IDebugApplicationThreadEvents110 接口 |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadevents110-interface"></a>IDebugApplicationThreadEvents110 接口
将添加更多的线程事件。 这些事件仅是本地的。 也就是说，你可以订阅它们仅在进程正在调试，请使用[IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738)通知和取消方法通知上 PDM 应用程序线程对象 (对象实现[IDebugApplicationThread接口](../../winscript/reference/idebugapplicationthread-interface.md))。 它们出现在它们来自的线程。  
  
> [!IMPORTANT]
>  此接口由 PDM v11.0 和更高版本实现。 在 activdbg100.h 中发现。  
  
## <a name="methods"></a>方法  
 `IDebugActivationThreadEvents110` 接口公开以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|调用到使用 PDM 的线程的线程切换已开始。|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|线程从断点继续工作，并且将再次处于活动状态。|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|线程处于挂起状态的断点，可以处理需要完全挂起的线程的调用。|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|调用到使用 PDM 的线程的线程切换已完成。|