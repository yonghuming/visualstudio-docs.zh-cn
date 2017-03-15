---
title: "IDebugExpressionEvaluator2::GetService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::GetService"
  - "GetService"
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索给定的服务对象的唯一标识符。  
  
## 语法  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```c#  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### 参数  
 `uid`  
 \[in\] 检索的服务的唯一标识符。  
  
 `ppService`  
 \[out\] 返回表示一个服务的对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 这可能是一个第三方表达式计算器使用从另一个表达式计算器的服务。  例如，此方法可用于获取可视化工具服务的接口从默认表达式计算器。  第三方表达式计算器不大可能需要实现此接口。  
  
## 请参阅  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)