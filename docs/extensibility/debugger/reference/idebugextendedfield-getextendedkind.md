---
title: "IDebugExtendedField::GetExtendedKind | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExtendedField::GetExtendedKind"
  - "GetExtendedKind"
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExtendedField::GetExtendedKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索指定的扩展的字段类型。  
  
## 语法  
  
```cpp#  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```c#  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### 参数  
 `pdwKind`  
 \[in, out\] 从定义此字段的 [FIELD\_KIND\_EX](../../../extensibility/debugger/reference/field-kind-ex.md) 枚举值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)