---
title: "IActiveScript |Microsoft 文档"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
提供初始化脚本引擎所必需的方法。 脚本引擎必须实现`IActiveScript`接口。  
  
## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|通知的脚本引擎[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)主机提供的站点。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|检索与 Windows 脚本引擎关联的站点对象。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|将脚本引擎放入指定的状态。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|检索脚本引擎的当前的状态。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|使脚本引擎放弃任何当前加载的脚本，丢失其状态，并释放任何它具有对其他对象，因此输入已关闭的状态的接口指针。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|将根级别项的名称添加到脚本引擎的命名空间。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|将类型库添加到脚本的命名空间。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|检索`IDispatch`正在运行的脚本的接口。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|检索当前正在执行的线程的脚本引擎定义标识符。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|检索与给定的 Microsoft Win32 线程关联的线程的脚本引擎定义标识符。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|检索脚本线程的当前状态。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|中断正在运行的脚本线程的执行。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|克隆当前脚本引擎 （减去任何当前执行状态），返回当前线程中没有站点加载脚本引擎。|  
  
## <a name="see-also"></a>另请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)