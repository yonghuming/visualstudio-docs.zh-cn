---
title: "IDebugDocumentHost::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetPathName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetPathName"
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetPathName
返回文档源文件的完整路径和文件名。  
  
## 语法  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### 参数  
 `pbstrLongName`  
 \[in\]包含长名称的字符串。  
  
 `pfIsOriginalFile`  
 \[out\]为true的标志，如果 `pbstrLongName` 引用的是文档的原始文件，错误否则为。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|不能创建或确定源文件。|  
  
## 备注  
 此方法返回文档源文件的完整路径和文件名。  
  
## 请参阅  
 [IDebugDocumentHost 接口](../../winscript/reference/idebugdocumenthost-interface.md)