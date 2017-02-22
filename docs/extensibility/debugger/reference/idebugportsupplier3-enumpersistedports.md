---
title: "IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs"
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
  - "IDebugPortSupplier3::EnumPersistedPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3::EnumPersistedPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法检索允许持久的端口列出了枚举的对象。  
  
## 语法  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### 参数  
 `PortNames`  
 \[in\] 包含端口名列表在保持的端口中查找并返回的 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 结构。  仅保留具有这些名称的端口将返回。  
  
 `ppEnum`  
 \[out\] 对象实现 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 保留的端口加载，当端口提供实例化时，并保存何时销毁端口提供程序。  
  
## 请参阅  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)