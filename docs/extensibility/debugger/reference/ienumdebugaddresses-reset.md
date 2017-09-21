---
title: "IEnumDebugAddresses::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Reset"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Reset 方法"
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法重置枚举到第一个元素。  
  
## 语法  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### 参数  
 无  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法调用之后，下调用 [下一步](../Topic/IEnumDebugAddresses::Next.md) 返回枚举中的第一个元素。  
  
## 请参阅  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [下一步](../Topic/IEnumDebugAddresses::Next.md)