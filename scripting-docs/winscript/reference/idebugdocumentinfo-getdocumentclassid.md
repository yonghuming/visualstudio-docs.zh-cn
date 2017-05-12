---
title: "IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentInfo.GetDocumentClassId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentInfo::GetDocumentClassId"
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentInfo::GetDocumentClassId
返回标识文件类型的 `CLSID`。  
  
## 语法  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### 参数  
 `pclsidDocument`  
 \[in\]一个标识文件类型的 `CLSID`。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法允许调试器IDE中承载此的自定义浏览器文档。  
  
 如果文档没有可见的数据，`pclsidDocument` 的返回值为 `CLSID_NULL`。  
  
## 请参阅  
 [IDebugDocumentInfo 接口](../../winscript/reference/idebugdocumentinfo-interface.md)