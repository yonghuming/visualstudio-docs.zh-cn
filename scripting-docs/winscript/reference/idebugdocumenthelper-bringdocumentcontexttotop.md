---
title: "IDebugDocumentHelper::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.BringDocumentContextToTop
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::BringDocumentContextToTop"
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::BringDocumentContextToTop
将此的上下文在调试器用户界面的顶级文档。  
  
## 语法  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### 参数  
 `pddc`  
 文档上下文对调试器用户界面的顶部显示。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法将此的上下文在调试器用户界面的顶级文档。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)