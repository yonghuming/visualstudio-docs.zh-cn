---
title: "IDebugDefaultPort2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::GetServer"
helpviewer_keywords: 
  - "IDebugDefaultPort2::GetServer"
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取一个接口。服务器此端口打开。  
  
## 语法  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```c#  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### 参数  
 `ppServer`  
 \[out\] 返回实现 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 接口的对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 由 Visual Studio 实现表示服务所在的服务器端口。  
  
## 请参阅  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)