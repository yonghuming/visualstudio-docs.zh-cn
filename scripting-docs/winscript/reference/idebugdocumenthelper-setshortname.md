---
title: "IDebugDocumentHelper::SetShortName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetShortName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetShortName"
ms.assetid: 811a444b-0ea4-4374-9d4c-4f7713bdd1ff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetShortName
设置短名称文档。  
  
## 语法  
  
```  
HRESULT SetShortName(  
   LPCOLESTR  pszShortName  
);  
```  
  
#### 参数  
 `pszShortName`  
 \[in\]一个Null终止的包含文档的短名称的字符串。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法设置新的短名称文档。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)