---
title: "获取一个端口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "获取的端口"
  - "调试 [调试 SDK]，端口"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 获取一个端口
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

端口表示与进程运行的计算机的连接。  该计算机可以是本地计算机或可能运行基于非 windows 操作系统的远程计算机 \(;请参见 [端口](../../extensibility/debugger/ports.md) 有关更多信息\)。  
  
 端口。 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 接口表示。  它用于获取有关进程运行在端口连接的计算机。  
  
 调试引擎需要访问端口以便注册过程节点的访问与端口，并满足请求进行处理的信息。  例如，因此，如果调试引擎 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) 实现接口， [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) 实现方法可以请求端口一定返回的进程信息。  
  
 Visual Studio 提供必要的端口的调试引擎，，并接收来自端口提供程序的此端口。  如果程序附加 \(从调试器的内部或由于已引发异常，触发 JIT 实时 \[\] 对话框\)，使用户对于端口提供程序\) 使用的传输 \(其他名称选择。  否则，因此，如果用户启动程序从调试器中，项目系统指定端口提供程序使用。  在任何情况下， Visual Studio 实例化端口提供程序，由 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 接口，并将请求新的端口通过调用与 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 接口的 [添加端口](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 。  此端口然后将到一个窗体或其他窗体中的调试引擎。  
  
## 示例  
 此代码片段在 [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)演示如何使用端口提供给注册的 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 程序节点。  参数不直接使用此概念相关为清楚起见省略。  
  
> [!NOTE]
>  此示例使用端口生成和还原过程假定， [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) 接口位于端口实现。  控件绝不是唯一一种可以执行这些任务，并且，可能的端口甚至可能并非是包含的除了具有程序的 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 为之外它。  
  
```cpp#  
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
  
## 请参阅  
 [注册程序](../../extensibility/debugger/registering-the-program.md)   
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [端口供应商](../../extensibility/debugger/port-suppliers.md)   
 [端口](../../extensibility/debugger/ports.md)