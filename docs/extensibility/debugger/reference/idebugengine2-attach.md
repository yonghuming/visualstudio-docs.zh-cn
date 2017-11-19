---
title: "IDebugEngine2::Attach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::Attach
helpviewer_keywords: IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c31e4c8367c1ceba5a4692438e8c1f1503f4f63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
将调试引擎 (DE) 附加到的程序或程序。 由会话调试管理器 (SDM) DE 进程到 SDM 时调用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pProgram`  
 [in]数组[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)表示程序要附加到的对象。 这些是端口程序。  
  
 `rgpProgramNodes`  
 [in]数组[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)对象，表示程序节点，一个用于每个程序。 此数组中的程序节点表示为中的相同程序`pProgram`。 以便 DE 可以确定要将附加到的程序提供程序节点。  
  
 `celtPrograms`  
 [in]程序和/或程序中的节点数`pProgram`和`rgpProgramNodes`数组。  
  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)对象用于将调试事件发送到 SDM。  
  
 `dwReason`  
 [in]取值范围为[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)枚举，用于指定附加这些程序的原因。 有关详细信息，请参阅“备注”部分。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 有三个原因将附加到程序中，如下所示：  
  
-   `ATTACH_REASON_LAUNCH`指示，DE 附加到程序中，因为用户启动包含它的进程。  
  
-   `ATTACH_REASON_USER`指示用户已显式请求 DE 将附加到程序 （或包含的程序的过程）。  
  
-   `ATTACH_REASON_AUTO`指示 DE 附加到特定的程序，因为它已调试其他程序在特定的进程中。 这也称为自动附加。  
  
 当调用此方法时，DE 需要将这些事件发送序列中：  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) （如果它不已发送的特定实例的调试引擎）  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 此外，如果附加的原因是`ATTACH_REASON_LAUNCH`，DE 需要发送[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)事件。  
  
 一次 DE 获取[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)对象对应于正在调试的程序可以为任何私有接口对其进行查询。  
  
 在调用由给定数组中的程序节点的方法之前`pProgram`或`rgpProgramNodes`，模拟，如有必要，应上启用`IDebugProgram2`表示程序节点的接口。 通常情况下，但是，此步骤不需要。 有关详细信息，请参阅[安全问题](../../../extensibility/debugger/security-issues.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)