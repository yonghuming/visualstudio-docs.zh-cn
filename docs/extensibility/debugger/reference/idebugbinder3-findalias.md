---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "IDebugBinder3::FindAlias 方法"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法定位到一个别名，给定名称。  这将搜索过程中的所有别名。  
  
## 语法  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### 参数  
 `pcstrName`  
 \[in\] 查找的别名的名称。  
  
 `ppAlias`  
 \[out\] [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 接口时 \(如果有\) 表示的别名。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` \(如果未找到别名\) 或错误代码。  
  
## 备注  
 此方法在调用之前初始化为空目标对象;然后其后测试 null 值确定是否找到别名。  
  
## 请参阅  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)