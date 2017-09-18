---
title: "注册程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程序登记"
  - "调试 [调试 SDK]，程序注册"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 注册程序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在调试引擎捕获了一个端口，由 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 接口，在启用下一个步骤之后要调试的程序是注册其与端口。  在注册，程序的调试可通过以下方式之一:  
  
-   附加的进程，允许调试器在完整的调试到正在运行的应用程序控制。  
  
-   实时 \(JIT\)调试，使程序能够在以后的情况调试独立于调试器运行。  当运行时体系结构查看错误时，调试器在操作系统之前通知或运行时环境释放出错的程序的内存和资源。  
  
## 注册程序  
  
#### 注册程序  
  
1.  调用 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 方法执行由端口。  
  
     `IDebugPortNotify2::AddProgramNode` 需要指向 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 接口。  
  
     通常，那么，当该操作系统或运行时环境加载一个程序时，它将创建程序节点。  如果调试引擎 \(DE\)请求加载程序因此、创建和注册程序节点。  
  
     下面的示例演示启动程序和注册它。端口的调试引擎。  
  
    > [!NOTE]
    >  这不是唯一的方式生成和还原处理;这是注册端口的程序的主要示例。  
  
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
 [获取一个端口](../../extensibility/debugger/getting-a-port.md)   
 [启用要进行调试的程序](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)