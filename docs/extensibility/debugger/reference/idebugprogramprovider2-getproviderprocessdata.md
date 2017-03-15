---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

从检索运行程序列表中指定的进程。  
  
## 语法  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### 参数  
 `Flags`  
 \[in\] 标志的组合。 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 枚举的。  下面的标志。这是典型的调用:  
  
|Flag|说明|  
|----------|--------|  
|`PFLAG_REMOTE_PORT`|调用方在远程计算机上运行。|  
|`PFLAG_DEBUGGEE`|调用方当前正在调试 \(有关排列的其他信息。每个节点都将返回\)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|调用方附加到，但未由调试器启动。|  
|`PFLAG_GET_PROGRAM_NODES`|调用方请求程序节点列表返回。|  
  
 `pPort`  
 \[in\] 调用过程的端口运行。  
  
 `processId`  
 \[in\] 保存包含相关的程序进程的 ID 的 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构。  
  
 `EngineFilter`  
 \[in\] 数组 GUID 为调试分配的引擎调试此过程 \(这些属性将用于筛选实际返回基于的程序所提供的引擎;如果引擎未指定，则所有过程将返回\)。  
  
 `pProcess`  
 \[out\] 用请求的信息填充的 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 结构。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法由进程通常称为获取运行由于的程序进程列表。  返回的信息是 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象的列表。  
  
## 请参阅  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)