---
title: "IDebugDocumentHost::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetFileName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetFileName"
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetFileName
返回文档的名称，而不用路径信息。  
  
## 语法  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### 参数  
 `pbstrShortName`  
 \[in\]包含文档的短名称的字符串。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回文档的短名称，而不用路径信息。  该短名称通常用于情况下\(如 **保存…** 对话框。  
  
## 请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)