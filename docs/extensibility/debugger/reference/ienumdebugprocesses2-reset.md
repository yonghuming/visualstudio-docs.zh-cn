---
title: "IEnumDebugProcesses2::Reset |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugProcesses2::Reset
helpviewer_keywords: IEnumDebugProcesses2::Reset
ms.assetid: 31cbde4f-0bba-497a-9969-d2c342ef4a7b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 09d7579db900e3ec3afb8c2669dfac4fd2c0353f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugprocesses2reset"></a>IEnumDebugProcesses2::Reset
将枚举重置为第一个元素。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 调用此方法，对下一个调用后[下一步](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)方法返回的枚举的第一个元素。  
  
## <a name="see-also"></a>另请参阅  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)