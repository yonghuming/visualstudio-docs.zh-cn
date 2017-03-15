---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugAlias::GetICorDebugValue 方法"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索一个托管的代码界面，表示与此别名相关联的值。  
  
## 语法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### 参数  
 `ppUnk`  
 \[out 一个\] `IUnknown` 表示与此别名相关联的值的接口。 此接口可查询 `ICorDebugValue` 接口。  
  
## 返回值  
 如果成功，返回，则为 S\_OK;否则，返回错误代码。  
  
## 备注  
 此方法仅适用于托管的值 \( `ICorDebugValue` 是一个接口位于 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] 中定义和 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] cordebug.idl 文件中的 SDK\)。  
  
## 请参阅  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)