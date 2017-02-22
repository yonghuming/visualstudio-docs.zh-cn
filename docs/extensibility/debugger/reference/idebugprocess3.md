---
title: "IDebugProcess3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3"
helpviewer_keywords: 
  - "IDebugProcess3 接口"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示正在运行的进程及其程序。  此接口存在作为替换为在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口的方法。  它提供对所有程序的控件在处理。  
  
> [!NOTE]
>  [继续](../../../extensibility/debugger/reference/idebugprogram2-continue.md)、 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)和 [单步执行](../../../extensibility/debugger/reference/idebugprogram2-step.md) 方法已弃用，因此不应再使用。  使用在 `IDebugProcess3` 接口的相应方法。  
  
## 语法  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## 实现者说明  
 此接口由自定义端口提供程序实现托管程序作为组。  当程序管理作为组时，可以控制其执行并建立表达式计算器的一种语言。  必须由端口提供程序实现此接口。  
  
## 调用方的说明  
 此接口主要由该会话调用调试管理器 \(SDM\)为了在中标识程序的一组进程交互。  
  
 调用 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 接口的 [QueryInterface](/visual-cpp/atl/queryinterface) 获取此接口。  
  
## 方法按 Vtable 顺序  
 除了从 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)继承的方法之外， `IDebugProcess3` 执行以下操作方法。  
  
|方法|说明|  
|--------|--------|  
|[继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|继续执行或逐句通过处理。|  
|[执行](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|启动进程的执行。|  
|[单步执行](../../../extensibility/debugger/reference/idebugprocess3-step.md)|进度一个命令或语句在处理。|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|获取处理用于调试生成的原因。|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|设置此类型主语言，以便调试引擎可以将相应的表达式计算器。|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|检索为此当前设置的语言处理。|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|禁用此编辑并继续 " \(ENC\) 处理。<br /><br /> 自定义端口提供程序不执行此方法 \(它应始终返回 `E_NOTIMPL`\)。|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|此的 ENC 状态过程的访问。<br /><br /> 自定义端口提供程序不执行此方法 \(它应始终返回 `E_NOTIMPL`\)。|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|检索数组可用的唯一标识符调试引擎。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 请参阅  
 [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)