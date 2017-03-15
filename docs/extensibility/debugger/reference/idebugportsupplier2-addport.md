---
title: "IDebugPortSupplier2::AddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::AddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::AddPort"
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

添加一个端口。  
  
## 语法  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```c#  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### 参数  
 `pRequest`  
 \[in\] 描述要添加的端口的 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 对象。  
  
 `ppPort`  
 \[out\] 返回表示端口的 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法实际创建请求的端口以及添加到内部端口的提供程序的列表有效的端口。  [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 方法可以首先调用来避免可能的耗时的延迟。  
  
## 请参阅  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)