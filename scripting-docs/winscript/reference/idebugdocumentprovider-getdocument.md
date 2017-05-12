---
title: "IDebugDocumentProvider::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentProvider::GetDocument"
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider::GetDocument
如果它已不存在，使文档实例化。  
  
## 语法  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### 参数  
 `ppssd`  
 \[in\]调试文档与文档相对应。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 如果它已不存在，此方法使文档实例化。  
  
## 请参阅  
 [IDebugDocumentProvider 接口](../../winscript/reference/idebugdocumentprovider-interface.md)