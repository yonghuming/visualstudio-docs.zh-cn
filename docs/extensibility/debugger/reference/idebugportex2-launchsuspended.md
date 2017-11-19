---
title: "IDebugPortEx2::LaunchSuspended |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::LaunchSuspended
helpviewer_keywords: IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a65c7a8bbf7e3ec0dba7506b435cfb39da07198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
将启动可执行文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>参数  
 `pszExe`  
 [in]若要启动的可执行文件的名称。 这可以是完整路径或相对于工作目录中指定`pszDir`参数。  
  
 `pszArgs`  
 [in]要传递到可执行文件的参数。 如果没有任何参数，则可能是 null 值。  
  
 `pszDir`  
 [in]由可执行文件的工作目录的名称。 如果没有工作目录是必需的则可能是 null 值。  
  
 `bstrEnv`  
 [in]以 null 结尾的字符串，跟附加 NULL 终止符的环境块。  
  
 `hStdInput`  
 [in]备用的输入流的句柄。 如果不需要重定向，则可能为 0。  
  
 `hStdOutput`  
 [in]备用输出流的句柄。 如果不需要重定向，则可能为 0。  
  
 `hStdError`  
 [in]备用错误输出流的句柄。 如果不需要重定向，则可能为 0。  
  
 `ppPortProcess`  
 [out]返回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)表示启动的进程的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法应启动的过程，因此它已挂起和未运行任何代码。 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)调用方法来继续执行过程。  
  
 此外可以从调试引擎启动程序。 有关详细信息，请参阅[启动程序](../../../extensibility/debugger/launching-a-program.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [启动程序](../../../extensibility/debugger/launching-a-program.md)