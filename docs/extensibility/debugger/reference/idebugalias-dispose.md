---
title: "IDebugAlias::Dispose | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::Dispose"
helpviewer_keywords: 
  - "IDebugAlias::Dispose 方法"
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugAlias::Dispose
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

标记删除的此别名。  
  
## 语法  
  
```cpp  
HRESULT Dispose();  
```  
  
```c#  
int Dispose();  
```  
  
#### 参数  
 无。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 对于此方法调用，别名不再可用。  
  
## 请参阅  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)