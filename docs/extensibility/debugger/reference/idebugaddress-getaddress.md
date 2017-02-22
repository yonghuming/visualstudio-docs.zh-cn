---
title: "IDebugAddress::GetAddress | Microsoft Docs"
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
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "IDebugAddress:GetAddress 方法"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

返回描述对象及其位置在其范围或容器中的结构。  
  
## 语法  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### 参数  
 `pAddress`  
 \[in, out\] 此方法填充的 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构传递给此方法，用合适的信息并填充。  此信息如何解释取决于信息返回值和符号处理程序。  有关详细信息，请参见 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)。  
  
## 请参阅  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)