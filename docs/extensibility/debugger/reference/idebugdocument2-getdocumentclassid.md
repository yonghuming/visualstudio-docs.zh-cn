---
title: "IDebugDocument2::GetDocumentClassID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2::GetDocumentClassID"
helpviewer_keywords: 
  - "IDebugDocument2::GetDocumentClassID"
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocument2::GetDocumentClassID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取文档的类标识符。  
  
## 语法  
  
```cpp#  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```c#  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### 参数  
 `pclsid`  
 \[out\] 返回作为文档的类 ID 的 GUID。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 类 GUID 可以用于实例化单个类的每个表示文档。  
  
## 请参阅  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)