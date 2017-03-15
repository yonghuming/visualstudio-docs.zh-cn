---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索特定程序的程序节点。  
  
## 语法  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
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
  
 `pPort`  
 \[in\] 调用过程的端口运行。  
  
 `processId`  
 \[in\] 保存包含相关的程序进程的 ID 的 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) 结构。  
  
 `guidEngine`  
 \[in\] 调试引擎的 GUID 程序附加 \(如果有\)。  
  
 `programId`  
 \[in\] 程序 ID 获取过程的节点。  
  
 `ppProgramNode`  
 \[out\] 表示请求的程序节点的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)