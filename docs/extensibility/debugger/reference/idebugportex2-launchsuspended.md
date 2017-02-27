---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

生成可执行文件。  
  
## 语法  
  
```cpp#  
HRESULT LaunchSuspended(   
   LPCOLESTR        pszExe,  
   LPCOLESTR        pszArgs,  
   LPCOLESTR        pszDir,  
   BSTR             bstrEnv,  
   DWORD            hStdInput,  
   DWORD            hStdOutput,  
   DWORD            hStdError,  
   IDebugProcess2** ppPortProcess  
);  
```  
  
```c#  
int LaunchSuspended(   
   string             pszExe,  
   string             pszArgs,  
   string             pszDir,  
   string             bstrEnv,  
   uint               hStdInput,  
   uint               hStdOutput,  
   uint               hStdError,  
   out IDebugProcess2 ppPortProcess  
);  
```  
  
#### 参数  
 `pszExe`  
 \[in\] 将生成的可执行文件的名称。  这是一个完整路径或相对在 `pszDir` 参数指定的工作目录。  
  
 `pszArgs`  
 \[in\] 通过将参数传递到可执行文件。  ; 如果没有参数，可能为 null 值。  
  
 `pszDir`  
 \[in\] 可执行文件使用的工作目录的名称。  ，如果不需要，可能为 null 值工作目录。  
  
 `bstrEnv`  
 \[in\] 环境块 null 终止的字符串，后跟一个附加 NULL 结束符。  
  
 `hStdInput`  
 \[in\] 设置为替换输入流的句柄。  ，如果不需要，可能为 0 重定向。  
  
 `hStdOutput`  
 \[in\] 设置为替换输出流的句柄。  ，如果不需要，可能为 0 重定向。  
  
 `hStdError`  
 \[in\] 对备用错误输出流的句柄。  ，如果不需要，可能为 0 重定向。  
  
 `ppPortProcess`  
 \[out\] 返回表示生成的处理的 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法应生成过程，使其挂起和未运行任何代码。  [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) 方法调用回收进程。  
  
 程序从调试引擎还会启动。  有关详细信息，请参见[下启动程序](../../../extensibility/debugger/launching-a-program.md)。  
  
## 请参阅  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [下启动程序](../../../extensibility/debugger/launching-a-program.md)