---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取端口的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### 参数  
 `pbstrPortName`  
 \[out\] 返回端口的名称。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 接口从调试包 \(客户端\) 通常通过对端口提供程序 \(服务器\) 获取与端口的连接。  调试包和端口提供程序知道端口的选择。  如果一个简单的字符串可以描述端口，则 `IDebugPortRequest2::GetPortName` 方法具有生成足够的信息连接。  否则，附加接口可由客户端提供，使用 `IDebugPortRequest2::QueryInterface`，可由服务器获取。  
  
## 请参阅  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)