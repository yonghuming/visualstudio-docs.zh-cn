---
title: "IDebugEvent2::GetAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2::GetAttributes"
helpviewer_keywords: 
  - "IDebugEvent2::GetAttributes"
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEvent2::GetAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取此的属性调试事件。  
  
## 语法  
  
```cpp#  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```c#  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### 参数  
 `pdwAttrib`  
 \[out\] 标志的组合。 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 枚举的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口对所有事件是通用的。  此方法描述操作的类型;例如，是异步该事件同步或并为其指定一个停止点的事件。  
  
## 请参阅  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)