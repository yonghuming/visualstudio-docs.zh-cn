---
title: "IDebugDocumentHelper::CreateDebugDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.CreateDebugDocumentContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::CreateDebugDocumentContext"
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::CreateDebugDocumentContext
创建新文档调试上下文。  
  
## 语法  
  
```  
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### 参数  
 `iCharPos`  
 \[in\]调试开始的位置文档内容。  
  
 `cChars`  
 \[in\]中的字符数。上下文。  
  
 `ppddc`  
 \[in\]新调试文档上下文。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法允许宿主创建新文档调试上下文。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)