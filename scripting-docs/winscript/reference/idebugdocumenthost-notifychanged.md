---
title: "IDebugDocumentHost::NotifyChanged | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.NotifyChanged
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::NotifyChanged"
ms.assetid: 33a4a54f-3bcb-4422-b3c0-bdbf46590f34
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::NotifyChanged
通知宿主文档源文件中保存了，并且应刷新其内容。  
  
## 语法  
  
```  
HRESULT NotifyChanged();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法以通知宿主文档源文件中保存了，并且应刷新其内容。  
  
## 请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)