---
title: "IDebugProgram3::ExecuteOnThread |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b75ee8c7b53e751f322ba41bc3f93e2542e192ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
执行调试程序。 线程返回以便在哪个线程执行程序时用户正在查看调试器信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 有三种不同方法，调试器可以恢复之后停止执行：  
  
-   执行： 取消任何以前的步骤，并运行直到下一个断点，依此类推。  
  
-   步骤： 取消任何旧的步骤，并运行新的步骤完成之前。  
  
-   继续： 再次运行，并保留任何旧的步骤活动。  
  
 线程传递给`ExecuteOnThread`确定哪个步骤取消时很有用。 如果你不知道运行的线程，执行将取消所有步骤。 知识的线程，只需取消活动线程的步骤。  
  
## <a name="see-also"></a>另请参阅  
 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)