---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
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
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

执行调试器程序。  线程返回提供线程用户看到，在执行程序的调试器信息。  
  
## 语法  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### 参数  
 `pThread`  
 \[in\] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 有三种不同的方式调试器可以在终止后继续执行:  
  
-   执行:撤消以前的所有步骤，并运行直至下一断点等等。  
  
-   步骤:请移除所有以前的步骤，然后运行，直到新的步骤完成。  
  
-   继续:再次运行，并保留所有以前的步骤激活。  
  
 线程传递给 `ExecuteOnThread` 很有用，在确定时取消哪个步骤。  如果您不知道线程上运行，请执行取消所有步骤。  线程的知识，只需移除在活动线程的步骤。  
  
## 请参阅  
 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)