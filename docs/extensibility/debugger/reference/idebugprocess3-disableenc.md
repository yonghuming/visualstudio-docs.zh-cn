---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
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
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法在它包含\) 的此显式禁用 " 编辑并继续处理 \(和所有过程。  自定义端口提供程序应始终返回 `E_NOTIMPL`。  
  
## 语法  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### 参数  
 `reason`  
 \[in\] 从 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 枚举的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
> [!NOTE]
>  自定义端口提供程序应始终返回 `E_NOTIMPL`。  
  
## 备注  
 一次，编辑并继续 " 对处理，则禁用可以通过重新启动处理仅重新启用。  
  
## 请参阅  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)