---
title: "IDebugDocumentContext::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentContext.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentContext::GetDocument"
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentContext::GetDocument
返回包含此上下文的文档。  
  
## 语法  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### 参数  
 `ppsd`  
 \[in\]包含此上下文的文档。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 `GetDocument` 方法返回包含此上下文的文档。  
  
## 请参阅  
 [IDebugDocumentContext 接口](../../winscript/reference/idebugdocumentcontext-interface.md)