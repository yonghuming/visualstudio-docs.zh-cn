---
title: "IDebugDocument2::GetName | Microsoft Docs"
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
  - "IDebugDocument2::GetName"
helpviewer_keywords: 
  - "IDebugDocument2::GetName"
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocument2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在多种形式之一获取文档的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```c#  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### 参数  
 `gnType`  
 \[in\] 从确定名称的类型返回的 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md) 枚举的值。  
  
 `pbstrFileName`  
 \[out\] 返回包含文档名称的字符串。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法可能，例如，返回文档的名称作为前缀或文件名的文件名甚至部分。  
  
## 请参阅  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME\_TYPE](../../../extensibility/debugger/reference/getname-type.md)