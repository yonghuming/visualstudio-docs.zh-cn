---
title: "IDebugPortEx2::GetPortProcessId |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::GetPortProcessId
helpviewer_keywords: IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 300f0553ee081dee8adc34ab48ce1989fc86e6c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
获取本身的端口的进程 ID。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pdwProcessId`  
 [out]返回本身的端口的物理进程 ID。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 Win32 运行时中例如，此方法通常调用 Win32 函数`GetCurrentProcessId`来获取物理进程 id。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)