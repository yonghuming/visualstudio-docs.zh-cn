---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript 接口"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
提供必要的方法中初始化脚本引擎。  脚本引擎必须实现 `IActiveScript` 接口。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|通知宿主提供的脚本引擎 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 站点。|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|检索站点对象与Windows脚本引擎。|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|将脚本引擎为指定的状态。|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|检索脚本引擎的当前状态。|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|使脚本引擎丢弃所有当前加载的脚本，丢失它们必须其他对象的其状态和释放任何接口指针，因此输入一个关闭状态。|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|添加一个根级项目的名称改为脚本引擎的命名空间。|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|添加一个类型库到脚本的命名空间。|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|检索该运行的脚本的 `IDispatch` 接口。|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|检索当前正在执行的线程的一个脚本引擎中定义的标识符。|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|检索线程的一个脚本引擎中定义的标识符与特定Microsoft Win32线程。|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|检索脚本线程的当前状态。|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|中断运行的脚本执行线程。|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|克隆当前脚本引擎\(减号任何当前执行状态\)，返回没有站点在当前线程上已加载的脚本引擎。|  
  
## 请参阅  
 [Windows 脚本接口参考](../../winscript/reference/windows-script-interfaces-reference.md)