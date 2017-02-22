---
title: "IDebugProcess3::GetENCAvailableState | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
helpviewer_keywords: 
  - "IDebugProcess3::GetENCAvailableState"
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取当前编辑并继续处理的状态。  自定义端口提供程序应始终返回 `E_NOTIMPL`。  
  
## 语法  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```c#  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### 参数  
 `pReason`  
 \[out\] 从 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 枚举的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
> [!NOTE]
>  自定义端口提供程序应始终返回 `E_NOTIMPL`。  
  
## 备注  
 此状态可能会受到 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)的影响。  
  
## 请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)