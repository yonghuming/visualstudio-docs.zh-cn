---
title: "IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

确定文档位置是否位于给定的包含文档。  
  
## 语法  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```c#  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### 参数  
 `pDoc`  
 \[in\] 表示包含的 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 对象文档候选对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 此方法主要在设置使用在 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 接口的断点。  加载文档，断点位置调用来确定文档是否包含此位置。  
  
## 请参阅  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)