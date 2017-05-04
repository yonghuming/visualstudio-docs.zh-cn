---
title: "活动脚本调试概述 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "活动脚本调试概述"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 活动脚本调试概述
事件脚本调试接口允许非特定语言，宿主非调试，并支持各种开发环境。  
  
 ![脚本宿主进程](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
图 1  
  
 一个非特定语言调试环境可以支持编程语言的任何编程语言或组合，而不会的特定知识任何这些语言。  调试环境还支持跨语言单步执行和断点。  \(本概述重点介绍主要支持脚本语言，例如 VBScript 和 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]。\)  
  
 一个主机非调试器可以自动用于任何操作脚本宿主，例如 Internet Explorer 或自定义宿主。  宿主控件哪些调试器提供给用户，将从文档节点构树的结构将内容，并调试的语法着色文档。  这允许正在调试的源代码公开宿主中文档。  例如，Internet Explorer 在 HTML 页中显示脚本。  
  
 在下面的小节，活动调试的每个主要组件及其关联的接口讨论。  但是，在将来前，必须定义多个键有效的调试概念：  
  
 Host Application — 宿主应用程序  
 承载脚本引擎并提供 scriptable 设置对象的应用程序 \(或“对象模型”\)。  
  
 语言引擎  
 提供分析元素，执行和调试抽象特定语言的。  
  
 调试器 IDE  
 通过通信提供调试 UI 与宿主应用程序和语言引擎的应用程序。  
  
 计算机进行管理器  
 维护可注册表的元素应用程序进程。  
  
 进程内调试管理器  
 维护节点构树可调试的元素为某个特定文档应用程序，跟踪正在运行的线程，等等。  
  
 文档上下文  
 文档上下文是表示在宿主的源代码的抽象一个指定范围。  
  
 代码上下文  
 代码上下文表示语言引擎 \(“虚拟指令指针”上运行代码中的特定位置。\)  
  
 表达式上下文  
 特定上下文 \(例如，堆栈帧\) 表达式可以由语言引擎计算。  
  
 浏览的对象  
 对象名的结构化，与语言无关的表示形式，类型、值和子对象，适用于实现“监视"窗口”UI。  
  
 下面每个概述键有效的调试组件和对应，关联的接口，后跟这些接口详细信息。  
  
## 语言引擎  
 语言引擎提供：  
  
-   语言分析和执行。  
  
-   调试支持 \(断点等\)。  
  
-   表达式计算。  
  
-   语法着色。  
  
-   浏览的对象。  
  
-   枚举堆栈和分析。  
  
 下面的脚本引擎需要支持调试、表达式浏览计算和对象的接口。  宿主应用程序使用这些接口映射在其之间由调试器 UI 文档上下文和引擎的代码上下文，并执行表达式计算、堆栈浏览枚举和的对象。  
  
 [IActiveScriptDebug 接口](../winscript/reference/iactivescriptdebug-interface.md)  
 提供语法着色和代码上下文枚举。  
  
 [IActiveScriptErrorDebug 接口](../winscript/reference/iactivescripterrordebug-interface.md)  
 returns 文档上下文和堆栈帧 false。  
  
 [IActiveScriptSiteDebug 接口](../winscript/reference/iactivescriptsitedebug-interface.md)  
 宿主提供了链接从脚本引擎到调试器。  
  
 [IDebugCodeContext 接口](../winscript/reference/idebugcodecontext-interface.md)  
 提供虚拟“指令指针”在线程。  
  
 [IEnumDebugCodeContexts 接口](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 枚举对应于文档上下文中的代码上下文。  
  
 [IDebugStackFrame 接口](../winscript/reference/idebugstackframe-interface.md)  
 表示在线程堆栈的逻辑堆栈帧。  
  
 [IDebugExpressionContext 接口](../winscript/reference/idebugexpressioncontext-interface.md)  
 提供可以在其中计算表达式的上下文。  
  
 [IDebugStackFrameSniffer 接口](../winscript/reference/idebugstackframesniffer-interface.md)  
 提供一种枚举逻辑堆栈帧。  
  
 [IDebugExpression 接口](../winscript/reference/idebugexpression-interface.md)  
 表示异步计算的表达式。  
  
 [IDebugSyncOperation 接口](../winscript/reference/idebugsyncoperation-interface.md)  
 允许脚本引擎将特定时需要执行，如果嵌套阻塞线程的操作。  
  
 [IDebugAsyncOperation 接口](../winscript/reference/idebugasyncoperation-interface.md)  
 提供同步异步访问调试操作。  
  
 [IDebugAsyncOperationCallBack 接口](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 提供状态事件与 `IDebugAsyncOperation` 接口计算的进度相关。  
  
 [IEnumDebugExpressionContexts 接口](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 枚举 `IDebugExpressionContexts` 对象的集合。  
  
 [IProvideExpressionContexts 接口](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 提供一种枚举特定元素的已知表达式上下文。  
  
 [IDebugFormatter 接口](../winscript/reference/idebugformatter-interface.md)  
 允许语言或 IDE 自定义在不同的值之间进行转换或 VARTYPE 类型和字符串。  
  
 [IDebugStackFrameSnifferEx 接口](../winscript/reference/idebugstackframesnifferex-interface.md)  
 枚举 PDM 的逻辑堆栈帧。  
  
## 宿主  
 宿主：  
  
-   承载语言引擎。  
  
-   提供对象模型 \(可以为其编写脚本\) 的对象集。  
  
-   定义可将调试及其内容的一个节点构树文档。  
  
-   组织脚本到虚拟应用程序。  
  
 具有两个主：  
  
-   一个沉默寡言的宿主支持基本操作脚本接口。  它不排列控件文档结构或组织；脚本完全取决于提供给语言引擎。  
  
-   一个智能宿主支持允许它定义文档节点构树的较大组接口，文档内容和语法着色。  有一组帮助器接口，描述在下小节，便于宿主是一个智能宿主。  
  
### 智能宿主帮助器接口  
 提供大大简化的 `IDebugDocumentHelper` 方法的一组接口宿主可以使用获取智能承载的优点，不处理最大复杂 \(和功能\) 的完整主机接口。  
  
 不需要当然宿主使用这些接口。  但是使用这些接口可以避免实现或使用多种更复杂的接口。  
  
 [IDebugDocumentHelper 接口](../winscript/reference/idebugdocumenthelper-interface.md)  
 实现由 PDM 以及个接口提供实现所需的智能承载。  
  
 [IDebugDocumentHost 接口](../winscript/reference/idebugdocumenthost-interface.md)  
 实现 \(可选\) 由宿主公开宿主特定功能，比如语法着色，在调试器。  
  
 有关更多信息，请参见[实现智能宿主帮助程序接口](../winscript/implementing-smart-host-helper-interfaces.md)。  
  
### 完整的智能主机接口  
 在下，如果不使用帮助器接口，该全套的接口智能宿主必须实现或使用。  
  
 宿主实现的接口：  
  
 [IDebugDocumentInfo 接口](../winscript/reference/idebugdocumentinfo-interface.md)  
 在文档提供信息，也可能不会实例化。  
  
 [IDebugDocumentProvider 接口](../winscript/reference/idebugdocumentprovider-interface.md)  
 用于实例化文档提供方法在需要时。  
  
 [IDebugDocument 接口](../winscript/reference/idebugdocument-interface.md)  
 所有的基接口调试文档。  
  
 [IDebugDocumentText 接口](../winscript/reference/idebugdocumenttext-interface.md)  
 提供对调试的只会写入版本文档。  
  
 [IDebugDocumentTextAuthor 接口](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 允许编辑调试的只会写入版本文档。  
  
 [IDebugDocumentContext 接口](../winscript/reference/idebugdocumentcontext-interface.md)  
 提供文档的一部分抽象表示正在调试的。  
  
 PDM 实现的接口委托宿主：  
  
 [IDebugApplicationNode 接口](../winscript/reference/idebugapplicationnode-interface.md)  
 通过提供在项目节点构树中的上下文扩展 `IDebugDocumentProvider` 接口的功能。  
  
## 调试器 IDE  
 IDE 是一个与语言无关调试 UI。  它提供：  
  
-   文档浏览器\/编辑器。  
  
-   断点管理。  
  
-   表达式计算和"监视"窗口。  
  
-   浏览的堆栈帧。  
  
-   浏览对象\/的选件类。  
  
-   浏览虚拟应用程序框架。  
  
 调试器实现的接口：  
  
 [IApplicationDebugger 接口](../winscript/reference/iapplicationdebugger-interface.md)  
 调试器 IDE 会话显示的主要接口。  
  
 [IApplicationDebuggerUI 接口](../winscript/reference/iapplicationdebuggerui-interface.md)  
 为外部组件到调试器的用户界面 \(UI\) 的多个控件。  
  
 [IDebugExpressionCallBack 接口](../winscript/reference/idebugexpressioncallback-interface.md)  
 为 `IDebugExpression` 计算进度提供状态事件。  
  
 [IDebugDocumentTextEvents 接口](../winscript/reference/idebugdocumenttextevents-interface.md)  
 提供指示的事件与关联的更改文本文档。  
  
 [IDebugApplicationNodeEvents 接口](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 为 `IDebugApplicationNode` 接口提供事件接口。  
  
### 计算机进行管理器  
 计算机进行管理器的反斜挂接点在虚拟应用程序和调试器之间通过维护和枚举活动虚拟应用程序列表中。  
  
 [IDebugSessionProvider 接口](../winscript/reference/idebugsessionprovider-interface.md)  
 生成正在运行的应用程序的调试会话。  
  
 [IMachineDebugManager 接口](../winscript/reference/imachinedebugmanager-interface.md)  
 在计算机上主界面调试管理器。  
  
 [IMachineDebugManagerCookie 接口](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 类似于 `IMachineDebugManager` 接口，但是，此接口支持调试 cookie。  
  
 [IMachineDebugManagerEvents 接口](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 更改在运行的应用程序列表中维护由计算机的信号调试管理器。  
  
 [IEnumRemoteDebugApplications 接口](../winscript/reference/ienumremotedebugapplications-interface.md)  
 枚举计算机上运行的应用程序。  
  
### 进程内调试管理器  
 PDM 执行以下操作：  
  
-   同步多个语言调试引擎。  
  
-   维护节点构树可调试文档。  
  
-   合并堆栈帧。  
  
-   坐标断点并跳出语言引擎中。  
  
-   跟踪线程。  
  
-   维护异步进程的调试器线程。  
  
-   的计算机进行通信调试管理器和调试器 IDE。  
  
 下列过程提供的接口调试管理器。  
  
 [IProcessDebugManager 接口](../winscript/reference/iprocessdebugmanager-interface.md)  
 为进程的主要接口调试管理器。  此接口可以从进程中创建，添加或移除虚拟应用程序。  
  
 [IRemoteDebugApplication 接口](../winscript/reference/iremotedebugapplication-interface.md)  
 表示正在运行的应用程序。  
  
 [IDebugApplication 接口](../winscript/reference/idebugapplication-interface.md)  
 供语言引擎和宿主使用的公开非远程调试方法。  
  
 [IRemoteDebugApplicationThread 接口](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 表示执行线程在特定应用程序中。  
  
 [IDebugApplicationThread 接口](../winscript/reference/idebugapplicationthread-interface.md)  
 允许语言引擎和宿主提供线程同步和维护线程特定的，调试状态信息。  
  
 [IEnumRemoteDebugApplicationThreads 接口](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 枚举在应用程序中运行的线程。  
  
 [IDebugThreadCall 接口](../winscript/reference/idebugthreadcall-interface.md)  
 封送的预定调用。  
  
 [IDebugApplicationNode 接口](../winscript/reference/idebugapplicationnode-interface.md)  
 保留文档的一个位置在层次结构。  
  
 [IEnumDebugApplicationNodes 接口](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 枚举节点的子节点与应用程序。  
  
 [IEnumDebugStackFrames 接口](../winscript/reference/ienumdebugstackframes-interface.md)  
 枚举堆栈帧与线程相对应，将从引擎。  
  
 [IDebugCookie 接口](../winscript/reference/idebugcookie-interface.md)  
 在脚本调试器允许调试 cookie 设置。  
  
 [IDebugHelper 接口](../winscript/reference/idebughelper-interface.md)  
 作为一个工厂用作对象浏览器和简单的脚本引擎连接点。  
  
 [ISimpleConnectionPoint 接口](../winscript/reference/isimpleconnectionpoint-interface.md)  
 提供描述提供了一种简单的方法，并枚举在特定激发的事件对于脚本引擎连接点。  
  
## 请参阅  
 [活动脚本调试器接口](../winscript/reference/active-script-debugger-interfaces.md)