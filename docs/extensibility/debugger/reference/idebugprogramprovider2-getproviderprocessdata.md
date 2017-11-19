---
title: "IDebugProgramProvider2::GetProviderProcessData |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords: IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae46cd5e90b4cdd23b0c7fafa147c43805974283
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
检索的从指定的进程中运行程序的列表。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>参数  
 `Flags`  
 [in]中的标志的组合[PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)枚举。 以下标志是典型的此调用：  
  
|Flag|描述|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|调用方远程计算机上运行。|  
|`PFLAG_DEBUGGEE`|当前正在调试调用方 （每个节点将返回有关封送处理的其他信息）。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|调用方已附加到但不是由调试器启动。|  
|`PFLAG_GET_PROGRAM_NODES`|调用方要求提供程序节点的列表，要返回。|  
  
 `pPort`  
 [in]调用进程的端口运行。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)保存包含的程序的进程 ID 问题的结构。  
  
 `EngineFilter`  
 [in]分配要调试该进程 （这些将用于筛选基于提供的引擎的支持; 如果未不指定任何引擎，则将返回所有程序实际都返回的程序） 的调试引擎的 Guid 数组。  
  
 `pProcess`  
 [out]A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)使用所需的信息填充的结构。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 此方法通常调用由进程以获取该进程中运行的程序的列表。 返回的信息是一份[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)对象。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)