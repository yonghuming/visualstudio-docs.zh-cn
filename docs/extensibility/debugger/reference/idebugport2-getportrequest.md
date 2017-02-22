---
title: "IDebugPort2::GetPortRequest | Microsoft Docs"
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
  - "IDebugPort2::GetPortRequest"
helpviewer_keywords: 
  - "IDebugPort2::GetPortRequest"
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取 \(如果有\) 以前用于创建端口端口的说明。  
  
## 语法  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```c#  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### 参数  
 `ppRequest`  
 \[out\] 返回表示用于创建端口的请求的 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  使用 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 端口，请求，因此，如果端口尚未创建返回 `E_PORT_NO_REQUEST` 。  
  
## 请参阅  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [添加端口](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)