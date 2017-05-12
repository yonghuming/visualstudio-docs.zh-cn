---
title: "IDebugDocumentHelper::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Attach"
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Attach
将此文档添加到文档树。  
  
## 语法  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### 参数  
 `pddhParent`  
 \[in\]文档的文档树中添加。  可以为 NULL。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法将此文档添加到文档树，使用 `pddhParent` 作为父级。  如果 `pddhParent` 是 `NULL`，文档将是顶级的文档。  
  
## 请参阅  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)