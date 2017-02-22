---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法通过调试引擎 \(DE\)生成过程。  
  
## 语法  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```c#  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### 参数  
 `pszMachine`  
 \[in\] 的生成过程的计算机的名称。  使用空值指定本地计算机上。  
  
 `pPort`  
 \[in\] 表示过程中运行的端口的 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 接口。  
  
 `pszExe`  
 \[in\] 将生成的可执行文件的名称。  
  
 `pszArgs`  
 \[in\] 通过将参数传递到可执行文件。  ; 如果没有参数，可能为 null 值。  
  
 `pszDir`  
 \[in\] 可执行文件使用的工作目录的名称。  ，如果不需要，可能为 null 值工作目录。  
  
 `bstrEnv`  
 \[in\] 环境块 null 终止的字符串，后跟一个附加 NULL 结束符。  
  
 `pszOptions`  
 \[in\] 可执行的选项。  
  
 `dwLaunchFlags`  
 \[in\] 为会话指定 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) 。  
  
 `hStdInput`  
 \[in\] 设置为替换输入流的句柄。  ，如果不需要，可能为 0 重定向。  
  
 `hStdOutput`  
 \[in\] 设置为替换输出流的句柄。  ，如果不需要，可能为 0 重定向。  
  
 `hStdError`  
 \[in\] 对备用错误输出流的句柄。  ，如果不需要，可能为 0 重定向。  
  
 `pCallback`  
 \[in\] 接收调试器事件的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 对象。  
  
 `ppDebugProcess`  
 \[out\] 返回表示生成的处理生成的 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 通常， [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 启动程序使用 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 方法随后将调试器附加到挂起的过程。  但是，在调试引擎可能需要启动程序的情况 \(例如，因此，如果调试引擎是正在调试的解释器和过程的一部分是一种解释语言\)，因此，在 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 使用 `IDebugEngineLaunch2::LaunchSuspended` 方法情况下。  
  
 ，在处理在挂起状态后，已成功生成了 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) 调用方法启动该进程。  
  
## 请参阅  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)