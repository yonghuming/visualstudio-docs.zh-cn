---
title: "IDebugDocumentInfo::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetName"
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetName
返回指定文档名称。  
  
## 语法  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### 参数  
 `dnt`  
 \[in\]类型的文档名称返回。  
  
 `pbstrName`  
 \[in\]包含名称的字符串。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|指定文档名称不知道。|  
  
## 备注  
 返回指定的此方案文档名称。  
  
## 请参阅  
 [IDebugDocumentInfo 接口](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE 枚举](../../winscript/reference/documentnametype-enumeration.md)