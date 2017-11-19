---
title: "获取一个端口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0645cefb4d102f976663bb4293454e2ae6318ad6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="getting-a-port"></a>获取端口
端口表示与在其运行进程的计算机的连接。 该计算机可以是本地计算机或远程计算机 (这无法可能运行非基于 Windows 的操作系统，请参阅[端口](../../extensibility/debugger/ports.md)有关详细信息)。  
  
 表示一个端口[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)接口。 它用于获取有关的端口连接到的计算机上运行的进程的信息。  
  
 调试引擎需要访问一个端口，以便注册端口的程序节点和满足对进程信息的请求。 例如，如果调试引擎实现[IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)接口的实现[GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)方法无法寻求必要的进程的端口要返回的信息。  
  
 Visual Studio 提供到调试引擎中，有必要的端口和端口供应商提供获取此端口。 如果程序附加到 （或从调试器中由于异常而引发了，随即将会触发在实时 [JIT] 对话框中），为用户提供选择的传输 （有关端口提供程序的另一个名称） 来使用。 否则，如果用户启动时从调试器中的程序，项目系统将指定的端口供应商联系，以使用。 在既情况下，Visual Studio 实例化端口供应商，由表示[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)接口，并通过调用要求提供一个新的端口[添加](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)与[IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)接口。 此端口然后将传递给一个窗体中的调试引擎或另一个。  
  
## <a name="example"></a>示例  
 此代码段演示如何使用的端口提供给[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)注册中的程序节点[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)。 为清楚起见，省略了此概念与不直接相关的参数。  
  
> [!NOTE]
>  此示例使用端口以启动并继续执行过程，并假定[IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)在端口上实现接口。 这决不是执行这些任务的唯一方法，并且可能，端口可能不甚至会涉及到不具有程序的[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)提供给它。  
  
```cpp  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [注册程序](../../extensibility/debugger/registering-the-program.md)   
 [启用要调试程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [端口供应商](../../extensibility/debugger/port-suppliers.md)   
 [端口](../../extensibility/debugger/ports.md)