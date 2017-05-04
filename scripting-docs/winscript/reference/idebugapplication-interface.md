---
title: "IDebugApplication 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication 接口"
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplication 接口
供语言引擎和宿主使用的公开非远程调试方法。  
  
 除了从 `IRemoteDebugApplication` 继承的方法之外，`IDebugApplication` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|设置应用程序的名称。|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|通知处理调试管理器一个语言引擎在单个步骤中模式下将返回到其调用方。|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|导致给定字符串由调试器IDE显示。|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|如果一个尚未附加开始，默认调试器IDE并附加调试会话对于此应用程序。|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|使当前线程阻塞并将断点的通知给调试器IDE。|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|导致此应用程序释放所有引用并输入一个非活动状态。|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|返回应用程序的当前中断标志。|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|返回线程与当前正在运行的线程。|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|提供对特定同步异步访问调试操作。|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|添加一个堆栈帧枚举器提供程序添加到此应用程序。|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|从此应用程序中移除堆栈帧枚举器提供程序。|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|确定当前正在运行的线程是在调试器线程。|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|为调用方提供框架运行在调试器线程的代码。|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|创建与特定文件提供程序的一个新的应用程序节点。|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|激发泛型事件对调试器的 `IApplicationDebugger` 接口。|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|使当前线程阻塞并将该错误的通知给调试器IDE。|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|确定一个点\(JIT\)调试器是否注册。|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|JIT确定调试器是否注册自动调试沉默寡言的主机。|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|添加一个全局表达式上下文提供程序添加到此应用程序。|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|从此应用程序中移除一个全局表达式上下文提供程序。|