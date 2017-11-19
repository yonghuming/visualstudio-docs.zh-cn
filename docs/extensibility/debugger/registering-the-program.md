---
title: "注册程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e0b0c883293cd01e21facfcc2e4483d2c5bbf164
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="registering-the-program"></a>注册程序
调试引擎已获取端口后，由[IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)接口，启用要调试程序的下一步是将其注册端口。 注册后，该程序是可用于调试通过以下方法之一：  
  
-   连接的过程，这使调试器能够获得的运行的应用程序的完整调试控制。  
  
-   在实时 (JIT) 调试时，它允许对进行事实后调试的一个独立于调试器运行程序。 当运行时体系结构捕获错误时，调试器通知操作系统之前或运行时环境释放的内存和出错的程序的资源。  
  
## <a name="registering-procedure"></a>注册过程  
  
#### <a name="to-register-your-program"></a>若要注册你的程序  
  
1.  调用[AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)端口由实现的方法。  
  
     `IDebugPortNotify2::AddProgramNode`需要指向的指针[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)接口。  
  
     通常，当操作系统或运行时环境加载程序时，它会创建程序节点。 如果需要加载该程序的调试引擎 (DE) DE 创建，并注册程序节点。  
  
     下面的示例演示启动程序并注册端口的调试引擎。  
  
    > [!NOTE]
    >  这不是唯一的方法来启动和恢复进程;这是主要与端口注册程序的一个示例。  
  
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
 [获取端口](../../extensibility/debugger/getting-a-port.md)   
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)