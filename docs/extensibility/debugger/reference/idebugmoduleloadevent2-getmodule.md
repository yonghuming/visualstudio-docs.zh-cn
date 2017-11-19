---
title: "IDebugModuleLoadEvent2::GetModule |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModuleLoadEvent2::GetModule
helpviewer_keywords: IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4bd5ebf74bb3818aff06e01b7c6d181760510f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
获取正在的模块加载或卸载。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pModule`  
 [out]返回[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)表示所加载或卸载的模块的对象。  
  
 `pbstrDebugMessage`  
 [在中，out]返回描述此事件的可选错误信息。 如果此参数为 null 值，不请求任何消息。  
  
 `pbLoad`  
 [在中，out]非零 (`TRUE`) 如果该模块加载和零 (`FALSE`) 如果正在卸载模块。 如果此参数为 null 值，请求无状态。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)