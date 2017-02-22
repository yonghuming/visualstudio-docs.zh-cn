---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetAddressesFromContext 方法"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法映射到文档上下文设置为数组调试地址。  
  
## 语法  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### 参数  
 `pDocContext`  
 \[in\] 文档上下文。  
  
 `fStatmentOnly`  
 \[in\] 如果为 true，调试到单个语句解决的限制。  
  
 `ppEnumBegAddresses`  
 \[out\] 返回启动的枚举数调试地址与此语句或行。  
  
 `ppEnumEndAddresses`  
 \[out\] 返回一个结束的一个 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 枚举数调试地址与此语句或行。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 文档上下文通常指示源行的大小。  此方法提供启动，然后关闭调试地址与这些行。  某些语言允许语句包含多个语句的跨多个行或行。  此方法提供一个标志限制调试地址到一个语句。  
  
 具有多个调试地址，在模板单个语句是可能的。  
  
## 请参阅  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)