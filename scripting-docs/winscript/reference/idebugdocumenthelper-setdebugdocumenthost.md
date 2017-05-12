---
title: "IDebugDocumentHelper::SetDebugDocumentHost | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDebugDocumentHost
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDebugDocumentHost"
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDebugDocumentHost
将此的 `IDebugDocumentHost` 文档。  
  
## 语法  
  
```  
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### 参数  
 `pddh`  
 \[in\]调试文档宿主。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 `IDebugDocumentHost` 接口为智能宿主语法着色使用，获取延迟，文本，并返回新创建的控件对象文档上下文。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)