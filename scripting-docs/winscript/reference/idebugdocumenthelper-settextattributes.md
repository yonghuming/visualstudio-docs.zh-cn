---
title: "IDebugDocumentHelper::SetTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetTextAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetTextAttributes"
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetTextAttributes
将文本范围的属性，重写该文本的其他属性。  
  
## 语法  
  
```  
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### 参数  
 `ulCharOffset`  
 \[in\]文本范围的开头的位置。  
  
 `cChars`  
 \[in\]中的字符数的大小。  
  
 `pstaTextAttr`  
 \[in\]文本范围的源文本属性。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 它是以前对文本范围的 `SetTextAttributes` 的错误文本添加到文档中。  调用 `AddDBCSText`、 `AddUnicodeText`或 `AddDeferredText` 方法将文本添加到文档中。  
  
## 请参阅  
 [IDebugDocumentHelper 接口](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR 枚举](../../winscript/reference/source-text-attr-enumeration.md)